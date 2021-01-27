## Fundamentals

> forgot where I got this from

Keep it simple, stupid. You ain't gonna need it.

You should think about what to do before you do it.

You should try to talk about what you’re planning to do before you do it.

You should think about what you did after you did it.

Be prepared to throw away something you’ve done in order to do something
different.

Always look for better ways of doing things.

“Good enough” isn’t good enough.


## Code

Code is a liability, not an asset. Aim to have as little of it as possible.

Build programs out of pure functions. This saves you from spending your brain
power on tracking side effects, mutated state and actions at a distance.

Use a programming language with a rich type system that lets you describe the
parts of your code and checks your program at compile time.

The expressivity of a programming language matters hugely. It’s not just a
convenience to save keypresses, it directly influences the way in which you
write code.

Have the same high standards for all the code you write, from little scripts to
the inner loop of your critical system.

Write code that is exception safe and resource safe, always, even in contexts
where you think it won’t matter. The code you wrote in a little ad-hoc script
will inevitably find its way into more critical or long-running code.

Use the same language for the little tools and scripts in your system too. There
are few good reasons to drop down into bash or Python scripts, and some
considerable disadvantages.

In code, even the smallest details matter. This includes whitespace and layout!


## Design

Model your domain using types.

Model your domain first, using data types and function signatures, pick
implementation technologies and physical architecture later.

Modelling - the act of creating models of the world - is a crucial skill, and
one that’s been undervalued in recent years.

Implement functionality in vertical slices that span your whole system, and
iterate to grow the system.

Resist the temptation to use your main domain types to describe interfaces or
messages exchanged by your system. Use separate types for these, even if it
entails some duplication, as these types will evolve differently over time.

Prefer immutability always. This applies to data storage as well as in-memory
data structures.

When building programs that perform actions, model the actions as data, then
write an interpreter that performs them. This makes your code much easier to
test, monitor, debug, and refactor.

Dependency management is crucial, so do it from day one. The payoff for this
mostly comes when your system is bigger, but it’s not expensive to do from the
beginning and it saves massive problems later.

Avoid circular dependencies, always.


## Quality

I don’t care if you write the tests first, last, or in the middle, but all code
must have good tests.

Tests should be performed at different levels of the system. Don’t get hung up
on what these different levels of tests are called.

Absolutely all tests should be automated.

Test code should be written and maintained as carefully as production code.

Developers should write the tests.

Run tests on the production system too, to check it’s doing the right thing.


## Designing systems

A better system is often a smaller, simpler system.

To design healthy systems, divide and conquer. Split the problem into smaller
parts.

Divide and conquer works recursively: divide the system into a hierarchy of
simpler sub-systems and components.
	
_Corollary: When designing a system, there are more choices than a monolith vs.
a thousand “microservices”._

The interface between parts is crucial. Aim for interfaces that are as small and
simple as possible.

Data dependencies are insidious. Take particular care to manage the coupling
introduced by such dependencies.

Plan to evolve data definitions over time, as they will inevitably change.

Asynchronous interfaces can be useful to remove temporal coupling between parts.

Every inter-process boundary incurs a great cost, losing type safety, an making
it much harder to reason about failures. Only introduce such boundaries where
absolutely necessary and where the benefits outweigh the cost.

Being able to tell what your system is doing is crucial, so make sure it’s
observable.

Telling what your system has done in the past is even more crucial, so make sure
it’s auditable.

A modern programming language is the most expressive tool we have for describing
all aspects of a system.

This means: write configuration as code, unless it absolutely, definitely has to
change at runtime.

Also, write the specification of the system as executable code.

And, use code to describe the infrastructure of your system, in the same
language as the rest of the code. Write code that interprets the description of
your system to provision actual physical infrastructure.

At the risk of repeating myself: everything is code.

_Corollary: if you’re writing JSON or YAML by hand, you’re doing it wrong. These
are formats for the machines, not for humans to produce and consume. (Don’t
despair though: most people do this, I do too, so you’re not alone! Let's just
try to aim for something better)._

The physical manifestation of your system (e.g. choices of storage, messaging,
RPC technology, packaging and scheduling etc) should usually be an
implementation detail, not the main aspect of the system that the rest is built
around.

It should be easy to change the underlying technologies (e.g. for data storage,
messaging, execution environment) used by a component in your system, this
should not affect large parts of your code base.

You should have at least two physical manifestations of your system: a fully
integrated in-memory one for testing, and the real physical deployment. They
should be functionally equivalent.

You should be able to run a local version of your system on a developer’s
computer with a single command. With the capacity of modern computers, there is
absolutely no rational reason why this isn’t feasible, even for big, complex
systems.

There is a running theme here: separate the description of _what_ a system does
from _how_ it does it. This is probably the single most important consideration
when creating a system.


## Building systems

For a new system, get a walking skeleton deployed to production as soon as
possible.

Your master branch should always be deployable to production.

Use feature branches if you like. Modern version control tools make merging easy
enough that it’s not a problem to let these be long-lived in some cases.

Ideally, deploy automatically to production on every update to master. If that’s
not feasible, it should be a one-click action to perform the deployment.

Maintain a separate environment for situations when you find it useful to test
code separately from production. Avoid more than one such extra environment, as
this introduces overheads and cost.

Prefer feature flags and similar mechanisms to control what's enabled in
production over separate test/staging environments and manual promotion of
releases.

Get in the habit of deploying from master to production from the very beginning
of a project. Doing this shapes both your system and how you work with it for
the better.

In fact, follow all these practices from the very beginning of a new system.
Retrofitting them later is much, much harder.


## Technology

Beware of hyped or fashionable technologies. The fundamentals of computer
science and engineering don’t change much over time.

Keep up with latest developments in technology to see how they can help you, but
be realistic about what they can do.

Choose your data storage backend according to the shape of data, types of
queries needed, patterns of writes vs. reads, performance requirements, and
more. Every use case is different.

That said, PostgreSQL should be your default and you should only pick something
else if you have a good reason.


## Teams

Hiring is the most critical thing you do in a team, so allocate time and effort
accordingly.

Use the smallest team possible, but no smaller.

Do everything you can to keep the team size small. Remove distractions for the
team, delegate work that isn’t crucial, provide tools that help their
productivity. Increasing the team size should be the last resort.

Teams need to be carefully grown, not quickly put together. When companies brag
about how many engineers they’re planning to hire in the near future, this is a
massive red flag.

New systems are best designed by a small numbers of minds, not committees. Once
the structure of the system is clear and the main decisions made, more people
can usefully get involved.

Code ownership may be undesirable, but it’s important to have someone who owns
the overall vision and direction for a system. Without it, the architecture will
degrade over time as it gets pulled in different directions.

Prefer paying more to get a smaller number of great people instead of hiring
more people at a lower salary.

Use contractors to bring in expertise, to ramp up a project quickly, for work on
trial projects, or to deal with specialised work of a temporary nature. Don’t
use contractors as a substitute for ordinary staff. (I say this as a
contractor.)

If you’re hiring contractors because you can’t get permanent staff, you’re not
paying your permanent staff enough.

As a team lead, if things go well, give your team the credit. If things go
badly, take the blame yourself.

A team member who isn’t a good fit for the team can kill the performance of the
whole team.

Inter-personal conflict is likewise poison to a team. While it may be possible
to resolve underlying issues, if it proves difficult, it’s usually better for
everyone to accept this and move people on.

Many people do “agile” badly, but that doesn’t mean that “agile” is bad.

Out of all the agile practices commonly used, estimating task sizes and trying
to measure project velocity is the least useful. (Its utility is often less than
zero).


## People

Be kind towards others, everyone faces their own battles no matter how they
appear externally.

Be kind to yourself. What you’re doing is hard, so accept that it sometimes
takes longer than you’d like and things don’t always work out.

Don't let your own desire to get things done quickly turn into undue pressure on
your peers.

The more certain people are about their opinions, the more you should take them
with a pinch of salt.

Imposter syndrome is a thing, as is the Dunning-Kruger effect. So judge people
on their contributions, not on how confident they seem.


## Personal development

Always keep learning.

Read papers (of the scientific variety).

Read the classics. So many “new” ideas in software development have actually
been around for decades.

Rest. Don’t work more than 8 hours a day. Get enough sleep. Have interests
outside your work.

Work efficiently instead of very long days. Try to remove distractions as much
as possible, for example pointless meetings. (As an aside, some meetings are
actually useful.)

When looking for a solution to a problem, don’t just pick the first one that
comes to mind. Learn to look for alternatives and evaluate them to find the best
choice.

Don’t work in isolation. Share ideas, talk new ideas and designs over with your
peers.

Don't be afraid to have strong opinions, but listen carefully to the opinions of
others too.