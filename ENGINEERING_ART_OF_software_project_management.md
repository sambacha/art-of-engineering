<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table of Contents

- [The purpose of software project management](#the-purpose-of-software-project-management)
  - [Two complimentary goals](#two-complimentary-goals)
  - [Estimating value and effort](#estimating-value-and-effort)
  - [Pivotal Tracker](#pivotal-tracker)
  - [Breaking down tasks](#breaking-down-tasks)
  - [Conclusion](#conclusion)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## The purpose of software project management

[source](https://blog.locut.us/2016/01/03/the-purpose-of-software-project-management/)

I recently read the article The sad graph of software death by Gregory Brown.

Brown describes a software project wherein tasks are being opened faster than
they are being closed in the project’s task tracker.  The author describes this
as “broken”, “sad”, and “wasteful.”  The assumption behind the article seems to
be that there is something inherently bad about tasks being opened faster than
they are being closed.

The author doesn’t explain why this is bad, and to me this article and the
confused discussion it prompted on Reddit are symptomatic of the fact that most
people don’t have a clear idea of the purpose of software project management.

Another symptom is that so many software projects run into problems, causing
tension between engineering, product, and other parts of the company.  It is
also the reason there is such a proliferation of tools that purport to help
solve the problem of project management, but none of them do because they don’t
start from a clear view of what exactly this problem is.

### Two complimentary goals

In my view, the two core goals of project management are prioritization and
predictability.

Prioritization ensures that at any given time, the project’s developers are
working on the tasks with the highest ratio of value to effort

Predictability means accurately estimating what will get done and by when, and
communicating that with the rest of the company.

A task tracker maintains a record of who is currently working on specific tasks,
which tasks are completed, and the future tasks that could be tackled. As such,
the trackers do not address the two core goals of project management directly.

I have actually thought about building a project management tool that addresses
these goals, i.e. prioritization and predictability, much more directly than is
currently the case with existing systems.  Unfortunately, to date the value to
effort ratio hasn’t been high enough relative to other projects 🙂

When a task is created or “opened” in a task tracker, this simply means “here is
something we may want to do at some point in the future.”

Opening a task isn’t, or shouldn’t be, an assertion that it must get done, or
must get done by a specific time. Although this might imply that some tasks may
never be finished, that’s ok. Besides, a row in a modern database table is very
cheap indeed.

Therefore, the faster rate at which tasks are opened rather than closed is not
an indication of a project’s impending demise; rather, it merely reflects the
normal tendency of people to think of new tasks for the project faster than
developers are able to complete those tasks.

Once created, tasks should then go through a prioritization or triage process;
however, the output isn’t simply “yes, we’ll do it” or “no, we won’t.”  Rather,
the output should be an estimate of the value provided to complete the task, as
well as an estimate of the effort or resources required to complete it. Based on
these two estimates, we can calculate the value/effort for the tasks.  It is
only then that we can stack-rank the tasks.

### Estimating value and effort

Of course, this makes it sound much simpler than it is.  Accurately estimating
the value of a task is a difficult process that may require input from sales,
product, marketing, and many other parts of a business.  Similarly, accurately
estimating the effort required to complete a task can be challenging for even
the most experienced engineer.

There are processes designed to help with these estimates.  Most of these
processes, such as planning poker, rely on the wisdom of crowds.  These are
steps toward the right direction.

I believe the ultimate solution to estimation will exploit the fact that people
are much better at making relative, rather than absolute, estimates. For
example, it is easier to guess that an elephant is 4 times heavier than a horse,
than to estimate that the absolute weight of an elephant is 8000 pounds.

This was recently supported by a simple experiment that I conducted.  First, I
asked a group to individually assign a number of these relative or comparative
estimates.  Then, I used a constraint solver to turn these into absolute
estimates.  The preliminary results are very promising.  This approach would
almost certainly be part of any project management tool that I might build.

Once we have good estimates for value/effort, we can then prioritize the tasks. 
Using our effort estimate, combined with an understanding of the resources
available, we can come up with better time estimates.  This will enhance
predictability that can be shared with the rest of the company.

### Pivotal Tracker

I have had quite a bit of experience with Pivotal Tracker, which I would
describe as the “least bad” project management tool. Pivotal Tracker doesn’t
solve the prioritization problem, but it does attempt to help with the
predictability problem.  Unfortunately, it does so in a way that is so
simplistic as to make it almost useless.  Let me explain.

Pivotal Tracker assumes that for each task, you have assigned effort estimates
which are in the form of “points” (you are responsible for defining what a point
means).   It also assumes that you have correctly prioritized the tasks, which
are then placed in the “backlog” in priority order.

Pivotal Tracker then monitors how many points are “delivered” within a given
time period.  It then uses these points to project when future tasks will be
completed.

The key problem with this tool is that it pretends that the backlog is static,
i.e. that new tasks won’t be added to the backlog before tasks are prioritized.
In reality, tasks are constantly being added to any active project, and these
new tasks might go straight to the top of the priority list.

Nevertheless, the good news is that Pivotal Tracker could probably be improved
to account for this addition of new tasks without much difficulty.  Perhaps a
third party could make these improvements by using the Java library I created
for integrating with PT’s API.   🙂

### Breaking down tasks

Most tasks start out as being quite large, and need to be broken down into
smaller tasks, both to make it easier to divide tasks among developers, but also
to improve the accuracy of estimates.

However, there isn’t much point in breaking down tasks when nobody is going to
start work on them for weeks or months.  For this reason, I advise setting
time-horizon limits for task sizes.  For example, you might say that a task that
is estimated to be started within three months can’t be larger than 2 man-weeks,
and a task to be started within 1 month cannot be larger than 4 man-days.

As a task crosses each successive time-horizon, it may need to be broken into
smaller tasks (each of which will, presumably, be small enough until they hit
the next time horizon).  In practice this can be accomplished with a weekly
meeting, that can be cancelled if there are no tasks to be broken down.  We
would assign one developer to break down each oversized task and then the
meeting would break up so that they could go and do that.  Typically each large
task would be broken down into 3-5 smaller tasks.

This approach has the additional advantage that it spreads out the process of
breaking down tasks over time and among developers.

Resource allocation

So how do you decide who works on what?  This is fairly simple under this
approach.  Developers simply pick the highest priority task that they can work
on (depending on skill set or interdependencies).

At OneSpot, when we broke down tasks, we left the subtasks in the same position
in the priority stack as the larger task they replaced.  Since developers pull
new tasks off the top of the priority list, this has the tendency to encourage
as many people as possible to be working on related tasks at any given time,
which minimizes the number of projects (large tasks) in-flight at any given
time.

### Conclusion

To conclude, without a clear view of the purpose of successful project
management, it is not surprising that so many projects flounder with many
project management tools failing to hit the mark. I hope I was able to provide
the beginnings of a framework to think about project management in a goal-driven
way.
