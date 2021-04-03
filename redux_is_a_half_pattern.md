---
title: Redux is half of a pattern.
description: Redux and State Machines
tags: 
---

[source: @davidkpiano](https://gist.github.com/davidkpiano)

Redux is fantastic.

Some of you might disagree, so here's the main reason why it's fantastic: over the last few years, it has popularized the idea of using message-passing to manage application state. Instead of making arbitrary method calls to various class instances or mutating data structures, we now can think of state as being in a "predictable container" that only changes as a reaction to these "messages."

It is universal enough to be used with any framework (or no framework at all), and has inspired libraries for other popular frameworks such as:

- [Vuex](https://vuex.vuejs.org/) for Vue
- [NgRx](https://ngrx.io/) for Angular

However, Redux has recently come under scrutiny by some prominent developers in the web community:

{% twitter 1191487232038883332 %}

{% twitter 1195126928799227905 %}

If you don't know these developers, they are the co-creators of Redux themselves. So why have Dan and Andrew, and many other developers, all but forsaken the use of Redux in applications?

The ideas and patterns in Redux appear sound and reasonable, and Redux is still used in many large-scale production apps today. However, it forces a certain architecture in your application: 

{% twitter 1025408731805184000 %}

As it turns out, this kind of single-atom immutable architecture is _not natural_ nor does it represent how any software application works (nor should work) in the real-world, as we will soon find out.

Redux is an alternative implementation of Facebook's [Flux "pattern"](https://facebook.github.io/flux). Many sticking points and hardships with Facebook's implementation have led developers to seek out alternative, nicer, more developer-friendly APIs such as Redux, Alt, Reflux, Flummox, [and many more.](https://github.com/kriasoft/react-starter-kit/issues/22). Redux emerged as a [clear winner](https://facebook.github.io/flux/docs/related-libraries/#redux---alternative-state-management), and it is stated that Redux combines the ideas from:

- [The Command pattern](https://www.wikiwand.com/en/Command_pattern)
- [The Elm Architecture](https://guide.elm-lang.org/architecture/)

However, not even the Elm architecture is a standalone architecture/pattern, as it is based on fundamental patterns, whether developers know it or not:

> Rather than someone inventing it, early Elm programmers kept discovering the same basic patterns in their code. It was kind of spooky to see people ending up with well-architected code without planning ahead!

In this post, I will highlight some of the reasons that Redux is _not_ a standalone pattern by comparing it to a fundamental, well-established pattern: the **finite state machine**.

I hope that some of these comparisons and differences will help you realize how some of the common pain points in Redux-driven applications materialize, and how you can use this existing pattern to help you craft a better state management architecture, whether you're using Redux or another library, or even another language.

## What is a finite state machine?

(Taken from another article I wrote, [The FaceTime Bug and the Dangers of Implicit State Machines](https://medium.com/@DavidKPiano/the-facetime-bug-and-the-dangers-of-implicit-state-machines-a5f0f61bdaa2)):

Wikipedia has a [useful but technical description](https://en.wikipedia.org/wiki/Finite-state_machine) on what a finite state machine is. In essence, a finite state machine is a computational model centered around states, events, and transitions between states. To make it simpler, think of it this way:

- Any software you make can be described in a **finite number of states** (e.g., `idle`, `loading`, `success`, `error`)
- You can only be in **one** of those states at any given time (e.g., you can’t be in the `success` and `error` states at the same time)
- You always start at some **initial state** (e.g., `idle`)
- You move from state to state, or **transition**, based on events (e.g., from the `idle` state, when the `LOAD` event occurs, you immediately transition to the `loading` state)

It’s like the software that you’re used to writing, but with more explicit rules. You might have been used to writing `isLoading` or `isSuccess` as Boolean flags before, but state machines make it so that you’re not allowed to have `isLoading === true && isSuccess === true` at the same time.

It also makes it _visually clear_ that event handlers can only do one main thing: forward their events to a state machine. They’re not allowed to “escape” the state machine and execute business logic, just like real-world physical devices: buttons on calculators or ATMs don’t actually do operations or execute actions; rather, they send "signals" to some central unit that manages (or _orchestrates_) state, and that unit decides what should happen when it receives that "signal".

## What about state that is not finite?

With state machines, especially [UML state machines (a.k.a. statecharts)](https://en.wikipedia.org/wiki/UML_state_machine), "state" refers to something different than the data that doesn't fit neatly into finite states, but both "state" and what's known as ["extended state"](https://en.wikipedia.org/wiki/UML_state_machine#Extended_states) work together.

For example, let's consider water 🚰. It can fit into one of four phases, and we consider these the _states_ of water:

- `liquid`
- `solid` (e.g., ice, frost)
- `gas` (e.g., vapor, steam)
- `plasma`

[![Water phase UML state machine diagram](https://www.uml-diagrams.org/examples/state-machine-example-water.png)](https://www.uml-diagrams.org/examples/water-phase-uml-state-machine-diagram-example.html)

> Water phase UML state machine diagram from [uml-diagrams.com](https://www.uml-diagrams.org/examples/water-phase-uml-state-machine-diagram-example.html)

However, the temperature of water is a _continuous_ measurement, not a discrete one, and it can't be represented in a finite way. Despite this, water temperature can be represented alongside the finite state of water, e.g.:

- `liquid` where `temperature === 90` (celsius)
- `solid` where `temperature === -5`
- `gas` where `temperature === 500`

There's many ways to represent the combination of finite and extended state in your application. For the water example, I would personally call the finite state `value` (as in the "finite state value") and the extended state `context` (as in "contextual data"):

```js
const waterState = {
  value: 'liquid', // finite state 
  context: {       // extended state
    temperature: 90
  }
}
```

But you're free to represent it in other ways:

```js
const waterState = {
  phase: 'liquid',
  data: {
    temperature: 90
  }
}

// or...

const waterState = {
  status: 'liquid',
  temperature: 90 // anything not 'status' is extended state
}
```

The key point is that there is a clear distinction between **finite** and **extended** state, and there is some logic that prevents the application from reaching an _impossible state_, e.g.:

```js
const waterState = {
  isLiquid: true,
  isGas: true,
  temperature: -50
}
```

And we can extend these examples to realistic code, such as changing this:

```js
const userState = {
  isLoading: true,
  isSuccess: false,
  user: null,
  error: null
}
```

To something like this:

```js
const userState = {
  status: 'loading', // or 'idle' or 'error' or 'success'
  user: null,
  error: null
}
```

## How does Redux compare to a finite state machine?

The reason I'm comparing Redux to a state machine is because, from a birds-eye view, their state management models look pretty similar. For Redux:

> `state` + `action` = `newState`

For state machines:

> `state` + `event` = `newState` + `effects`

In code, these can even be represented the same way, by using a [reducer](https://redux.js.org/basics/reducers/):

```js
function userReducer(state, event) {
  // Return the next state, which is
  // determined based on the current `state`
  // and the received `event` object

  // This nextState may contain a "finite"
  // state value, as well as "extended"
  // state values.

  // It may also contain side-effects
  // to be executed by some interpreter.
  return nextState;
}
```

There are already some subtle differences, such as "action" vs. "event" or how extended state machines model side-effects ([they do](https://en.wikipedia.org/wiki/UML_state_machine#Actions_and_transitions)). Dan Abramov even recognizes some of the differences:

{% twitter 1064661742188417029 %}

A reducer can be used to implement a finite state machine, but most reducers are _not_ modeled as finite state machines. Let's change that by learning some of the differences between Redux and state machines.

## Difference: finite & extended states

Typically, a Redux reducer's state will not make a clear distinction between "finite" and "extended" states, as previously mentioned above. This is an important concept in state machines: an application is always in _exactly one_ of a finite number of "states", and the rest of its data is represented as its extended state.

Finite states can be introduced to a reducer by making an explicit property that represents exactly one of the many possible states:

```js
const initialUserState = {
  status: 'idle',
  user: null,
  error: null
}
```

What's great about this is that, if you're using TypeScript, you can take advantage of using [discriminated unions](https://basarat.gitbooks.io/typescript/docs/types/discriminated-unions.html) to make impossible states impossible:

```js
interface User {
  name: string;
  avatar: string;
}

type UserState = 
  | { status: 'idle'; user: null; error: null; }
  | { status: 'loading'; user: null; error: null; }
  | { status: 'success'; user: User; error: null; }
  | { status: 'failure'; user: null; error: string; }
```

## Difference: events vs. actions

In [state machine terminology](https://en.wikipedia.org/wiki/UML_state_machine#Actions_and_transitions), an "action" is a side-effect that occurs as the result of a transition:

> When an event instance is dispatched, the state machine responds by **performing actions**, such as changing a variable, performing I/O, invoking a function, generating another event instance, or changing to another state.

This isn't the only reason that using the term "action" to describe something that causes a state transition is confusing; "action" also suggests something that needs to be done (i.e., a command), rather than something that just happened (i.e., an event).

So keep the following terminology in mind when we talk about state machines:

- An **event** describes something that occurred. Events trigger state transitions.
- An **action** describes a side-effect that should occur as a _response_ to a state transition.

The [Redux style guide](https://redux.js.org/style-guide/style-guide/) also directly suggests modeling actions as events:

> However, we recommend trying to treat actions more as "describing events that occurred", rather than "setters". Treating actions as "events" generally leads to more meaningful action names, fewer total actions being dispatched, and a more meaningful action log history.
> 
> _Source: [Redux style guide: Model actions as events, not setters](https://redux.js.org/style-guide/style-guide/#model-actions-as-events-not-setters)_

When the word "event" is used in this article, that has the same meaning as a conventional Redux action object. For side-effects, the word "effect" will be used.


## Difference: explicit transitions

Another fundamental part of how state machines work are **transitions**. A transition describes how one finite state transitions to another finite state due to an event. This can be represented using boxes and arrows:

![State machine describing login flow](https://thepracticaldev.s3.amazonaws.com/i/9cerj02qg66buqdmjrmq.png)

This diagram makes it clear that it's impossible to transition directly from, e.g., `idle` to `success` or from `success` to `error`. There are clear sequences of events that need to occur to transition from one state to another.

However, the way that developers tend to model reducers is by determining the next state solely on the received event:

```js
function userReducer(state, event) {
  switch (event.type) {
    case 'FETCH':
      // go to some 'loading' state
    case 'RESOLVE':
      // go to some 'success' state
    case 'REJECT':
      // go to some 'error' state
    default:
      return state;
  }
}
```

The problem with managing state this way is that it does not prevent _impossible transitions_. Have you ever seen a screen that briefly displays an error, and then shows some success view? If you haven't, browse [Reddit](https://reddit.com), and do the following steps:

1. Search for anything.
2. Click on the "Posts" tab while the search is happening.
3. Say "aha!" and wait a couple seconds.

In step 3, you'll probably see something like this (visible at the time of publishing this article):

![Screenshot of Reddit showing no search results](https://thepracticaldev.s3.amazonaws.com/i/6xmuf3flhekv65gsds79.png)

After a couple seconds, this unexpected view will disappear and you will finally see search results. This bug has been present for a while, and even though it's innocuous, it's not the best user experience, and it can definitely be considered faulty logic.

However it is implemented (Reddit _does_ use Redux...), something is definitely wrong: _an impossible state transition happened_. It makes absolutely no sense to transition directly from the "error" view to the "success" view, and in this case, the user shouldn't see an "error" view anyway because it's not an error; it's still loading!

You might be looking through your existing Redux reducers and realize where this potential bug may surface, because by basing state transitions only on events, these impossible transitions become possible to occur. Sprinkling if-statements all over your reducer might alleviate the symptoms of this:

```js
function userReducer(state, event) {
  switch (event.type) {
    case 'FETCH':
      if (state.status !== 'loading') {
        // go to some 'loading' state...
        // but ONLY if we're not already loading
      }
    
    // ...
  }
}
```

But that only makes your state logic harder to follow because the state transitions are _not explicit_. Even though it might be a little more verbose, it's better to determine the next state based on both the current finite state and the event, rather than just on the event:

```js
function userReducer(state, event) {
  switch (state.status) {
    case 'idle':
      switch (event.type) {
        case 'FETCH':
          // go to some 'loading' state

        // ...
      }
    
    // ...
  }
}
```

But don't just take my word for it. The Redux style guide also strongly recommends treating your reducers as state machines:

> [...] treat reducers as "state machines", where the combination of both the current state and the dispatched action determines whether a new state value is actually calculated, not just the action itself unconditionally.
>
> _Source: [Redux style guide: treat reducers as state machines](https://redux.js.org/style-guide/style-guide/#treat-reducers-as-state-machines)_

I also talk about this idea in length in my post: [No, disabling a button is not app logic.](https://dev.to/davidkpiano/no-disabling-a-button-is-not-app-logic-598i)

## Difference: declarative effects

If you look at Redux in isolation, its strategy for managing and executing side-effects is this:

> ¯\\\_(ツ)\_/¯

That's right; Redux has no built-in way of handling side-effects. In any non-trivial application, you _will_ have side-effects if you want to do anything useful, such as make a network request or kick off some sort of async process. Importantly enough, side-effects should _not_ be considered an afterthought; they should be treated as a first-class citizen and uncompromisingly represented in your application logic.

Unfortunately, with Redux, they are, and the only solution is to use [middleware](https://redux.js.org/advanced/middleware), which is inexplicably an advanced topic, despite being required for any non-trivial app logic:

> Without middleware, Redux store only supports synchronous data flow. 
> 
> _Source: https://redux.js.org/advanced/async-flow_

With extended/UML state machines (also known as statecharts), these side-effects are known as **actions** (and will be referred to as actions for the rest of this post) and are declaratively modeled. Actions are the direct result of a transition:

> When an event instance is dispatched, the state machine responds by **performing actions**, such as changing a variable, performing I/O, invoking a function, generating another event instance, or changing to another state.
> 
> _Source: [(Wikipedia) UML State Machine: Actions and Transitions](https://en.wikipedia.org/wiki/UML_state_machine#Actions_and_transitions)

This means that when an event changes state, actions (effects) may be executed as a result, even if the state stays the same (known as a "self-transition"). Just like Newton said:

> For every action, there is an equal and opposite reaction.
> 
> _Source: Newton's Third Law of Motion_

Actions _never_ occur spontaneously, without cause; not in software, not in hardware, not in real life, never. There is _always_ a cause for an action to occur, and with state machines, that cause is a state transition, due to a received event.

Statecharts distinguish how actions are determined in three possible ways:

- **Entry actions** are effects that are executed whenever a specific finite state is entered
- **Exit actions** are effects that are executed whenever a specific finite state is exited
- **Transition actions** are effects that are executed whenever a specific transition between two finite states is taken.

Fun fact: this is why statecharts are said to have the characteristic of both [Mealy machines](https://en.wikipedia.org/wiki/Mealy_machine) and [Moore machines](https://en.wikipedia.org/wiki/Moore_machine):

- With Mealy machines, "output" (actions) depends on the state and the event (transition actions)
- With Moore machines, "output" (actions) depends on just the state (entry & exit actions)

The original philosophy of Redux is that it did not want to be opinionated on how these side-effects are executed, which is why middleware such as [redux-thunk](https://github.com/reduxjs/redux-thunk) and [redux-promise](https://github.com/redux-utilities/redux-promise) exist. These libraries work around the fact that Redux is side-effect-agnostic by having third-party, use-case specific "solutions" for handling different types of effects.

So how can this be solved? It may seem weird, but just like you can use a  property to specify finite state, you can also use a property to specify _actions that should be executed_ in a declarative way:

```js
// ...
case 'FETCH':
  return {
    ...state,
    // finite state
    status: 'loading',
    // actions (effects) to execute
    actions: [
      { type: 'fetchUser', id: 42 }
    ]
  }
// ...
```

Now, your reducer will return useful information that answers the question, "what side-effects should be executed as a result of this state transition?" The answer is clear and colocated right in your app state: read the `actions` property for a declarative description of the actions to be executed, and execute them:

```js
// pretend the state came from a Redux React hook
const { actions } = state;

useEffect(() => {
  actions.forEach(action => {
    if (action.type === 'fetchUser') {
      fetch(`/api/user/${action.id}`)
        .then(res => res.json())
        .then(data => {
           dispatch({ type: 'RESOLVE', user: data });
        })
    }
  });
}, [actions]);
```

Having side-effects modeled declaratively in some `state.actions` property (or similar) has some great benefits, such as in predicting/testing or being able to trace when actions will or have been executed, as well as being able to customize the implementation details of executing those actions. For instance, the `fetchUser` action can be changed to read from a cache instead, all without changing any of the logic in the reducer.

## Difference: sync vs. async data flow

The fact is that middleware is indirection. It fragments your application logic by having it present in multiple places (the reducers and the middleware) without a clear, cohesive understanding of how they work together. Furthermore, it makes some use-cases easier but others much more difficult. For example: take this example from the [Redux advanced tutorial](https://redux.js.org/advanced/example-reddit-api), which uses `redux-thunk` to allow dispatching a "thunk" for making an async request:

```js
function fetchPosts(subreddit) {
  return dispatch => {
    dispatch(requestPosts(subreddit))
    return fetch(`https://www.reddit.com/r/${subreddit}.json`)
      .then(response => response.json())
      .then(json => dispatch(receivePosts(subreddit, json)))
  }
}
```

Now ask yourself: _how can I cancel this request?_ With `redux-thunk`, it simply isn't possible. And if your answer is to "choose a different middleware", you just validated the previous point. Modeling logic should not be a question of which middleware you choose, and middleware shouldn't even be part of the state modeling process.

As previously mentioned, the only way to model async data flow with Redux is by using middleware. And with all the possible use-cases, from thunks to Promises to sagas (generators) to epics (observables) and more, the ecosystem has plenty of different solutions for these. But the ideal number of solutions is _one_: the solution provided by the pattern in use.

Alright, so how do state machines solve the async data flow problem?

_They don't._

To clarify, state machines do not distinguish between sync and async data flows, because there is no difference. This is such an important realization to make, because not only does it simplify the idea of data flow, but it also models how things work in real life:

- A state transition (triggered by a received event) always occurs in "zero-time"; that is, states synchronously transition.
- Events can be received at any time.

There is no such thing as an asynchronous transition. For example, modeling data fetching doesn't look like this:

```
idle . . . . . . . . . . . . success
```

Instead, it looks like this:

```
idle --(FETCH)--> loading --(RESOLVE)--> success
```

Everything is the result of some event triggering a state transition. Middleware obscures this fact. If you're curious how async cancellation can be handled in a synchronous state transition manner, here's a couple of guiding points for a potential implementation:

- A cancellation intent is an _event_ (e.g., `{ type: 'CANCEL' }`)
- Cancelling an in-flight request is an _action_ (i.e., side-effect)
- "Canceled" is a state, whether it's a specific state (e.g., `canceled`) or a state where a request shouldn't be active (e.g., `idle`)

## Difference: local vs. global state

The first of [Redux's three principles](https://redux.js.org/introduction/three-principles) is that there is a _single source of truth_:

> The state of your whole application is stored in an object tree within a single store.
>
> _Source: [Redux's three principles: single source of truth](https://redux.js.org/introduction/three-principles#single-source-of-truth)_

The primary reason for this is that it makes many things _easier_, such as sharing data, rehydrating state, "time-travel debugging", etc. But it suffers from a fundamental contradiction: _there is no such thing as a single source of truth_ in any non-trivial application. All applications, even front-end apps, are distributed at some level:

{% twitter 1116019772238454784 %}

Whenever something is done for the sole purpose of making something easy, it almost always makes some other use-case more difficult. Redux and its single-source-of-truth is no exception, as there are many problems that arise from fighting against the nature of front-end apps being "distributed" instead of an idealistic atomic, global unit:

- Multiple orthogonal concerns that need to be represented in the state somehow. 

This is "solved" by using [`combineReducers`](https://redux.js.org/recipes/structuring-reducers/using-combinereducers)

- Multiple separate concerns that need to share data, communicate with each other, or are otherwise tangentially related.

This is "solved" by [more complex, custom reducers](https://redux.js.org/recipes/structuring-reducers/beyond-combinereducers) that orchestrate events through these otherwise separate reducers

- Irrelevant state updates: when separate concerns are combined (using `combineReducers` or similar) into a single store, whenever any part of the state updates, the _entire_ state is updated, and every "connected" component (every subscriber to the Redux store) is notified.

This is "solved" by using [selectors](https://redux.js.org/introduction/learning-resources#selectors), and perhaps by using another library like [`reselect`](https://blog.isquaredsoftware.com/2017/12/idiomatic-redux-using-reselect-selectors/) for memoized selectors.

I put "solved" in quotes because these are all solutions that are all but necessary due to problems that are caused solely by using a global, atomic store. In short, it's unrealistic, even for apps that are already using global stores. Whenever you use a 3rd-party component, or local state, or local storage, or query parameters, or a router, etc., you have already shattered the illusion of a single global store. App data is always distributed at some level, so the natural solution should be to embrace the distribution (by using local state) rather than fighting against it just for the sake of making some use-cases easier to develop in the short run.

## Acting differently

So how do state machines address this global state problem? To answer that, we need to zoom out a little bit and introduce another old, well-established model: [the actor model](https://en.wikipedia.org/wiki/Actor_model).

The actor model is a surprisingly simple model that can be extended slightly beyond its original purpose (concurrent computation). In short, an actor is an entity that can do three things:

- It can receive messages (events)
- It can change its state/behavior as a reaction to a received message, including spawning other actors
- It can send messages to other actors

If you thought "hmm... so a Redux store is sort of an actor", congratulations, you already have a good grasp on the model! A Redux store, which is based on some single combined reducer thing, can receive events, changes its state as a reaction to those events, but... it can't send messages to other stores (there's only one store) or between reducers (dispatching happens externally). It also can't really spawn other "actors", which makes the [Reddit example in the official Redux advanced tutorial](https://redux.js.org/advanced/async-actions) more awkward than it needs to be:

```js
function postsBySubreddit(state = {}, action) {
  switch (action.type) {
    case INVALIDATE_SUBREDDIT:
    case RECEIVE_POSTS:
    case REQUEST_POSTS:
      return Object.assign({}, state, {
        [action.subreddit]: posts(state[action.subreddit], action)
      })
    default:
      return state
  }
}
```

> _Source: https://redux.js.org/advanced/async-actions#reducersjs_

Let's dissect what is happening here:

1. We're taking only the relevant slice of state we need (`state[action.subreddit]`), which should ideally be its own entity
2. We are determining what the next state of only this slice should be, via `posts(state[action.subreddit], action)`
3. We are surgically replacing that slice with the updated slice, via `Object.assign(...)`.

In other words, there is no way we can dispatch or forward an event directly to a specific "entity" (or _actor_); we only have a single actor and have to manually update only the relevant part of it. Also, every other reducer in `combineReducers(...)` will get the entity-specific event, and even if they don't update, they will still be called for every single event. There's no easy way to optimize that. A function that isn't called is still much more optimal than a function that is called and ultimately does nothing.

So back on topic: how do state machines and actors fit together? Simply put, a state machine describes the behavior of an individual actor:

- Events are sent to a state machine (this is, after all, how they work)
- A state machine's state/behavior can change due to a received event
- A state machine can spawn actors and/or send messages to other actors (via executed actions)

This isn't a cutting-edge, groundbreaking model; in fact, you've probably been using the actor model (to some extent) without even knowing it! Consider a simple input component:

```jsx
const MyInput = ({ onChange, disabled }) => {
  const [value, setValue] = useState('');

  return (
    <input
      disabled={disabled}
      value={value}
      onChange={e => setvalue(e.target.value)}
      onBlur={() => onChange(value)}
    />
  );
}
```

This component, in an implicit way, is an actor!

- It "receives events" using React's slightly awkward parent-to-child communication mechanism - prop updates
- It changes state/behavior when an event is "received", such as when the `disabled` prop changes to `true` (which you can interpret as some event)
- It can send events to other "actors", such as sending a "change" event to the parent by calling the `onChange` callback (again, using React's slightly awkward child-to-parent communication mechanism)
- In theory, it can "spawn" other "actors" by rendering different components, each with their own local state.

## Multi-Redux?

Again, one of Redux's three main principles is that Redux exists in a single, global, atomic source of truth. All of the events are routed through that store, and the single huge state object is updated and permeates through all connected components, which use their selectors and memoization and other tricks to ensure that they are only updated when they need to be, especially when dealing with excessive, irrelevant state updates.

And using a single global store has worked pretty well when using Redux, right? Well... not exactly, to the point that there are entire libraries dedicated to providing the ability to use Redux on a more distributed level, e.g., for [component state and encapsulation](https://redux.js.org/introduction/ecosystem#component-state-and-encapsulation). It is possible to use Redux at a local component level, but that was not its main purpose, and the official `react-redux` integration does not naturally provide that ability.