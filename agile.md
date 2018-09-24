# [Agile Development](http://i.imgur.com/FcTiTuk.jpg)

Click on the title for a verbatim image from the meeting.

Further reading: 

* [The codeless code](http://thecodelesscode.com)
* [Methodology cancer](http://www.javacodegeeks.com/2014/04/development-methodologies.html)
* [The Five Whys](http://www.startuplessonslearned.com/2008/11/five-whys.html)

## "1. Defer building until pain"

This is also referred to as [kanban development](http://www.slideshare.net/JR0cket/jit-developmentwithkanbanjax-london2011).

### What is pain?

Pain [was the term used](https://therealwillet.hipchat.com/history/room/115122/2014/04/04?q=pain#14:12:55) to describe either one of these scenarios:

* customers' pain
* employees' pain
* developers' pain
* shareholders' pain

To identify pain, this strategy can be used:

> [A] part of the reason to focus on pain is that [pain] helps prioritize. 
> [The] top priorities likely come from pain [that] existing *customers* feel, or pain our *sales team* faces in getting new customers (sales, $)

> [I]f/when we are bringing on lots of new customers then we'll feel pain *internally*, and that will help us proritize making it fast/easy to bring new customers onboard

### Why defer building until pain?

This often happens with development:

* More urgent things come up
* There is always more to do
* There are hidden requirements
* Not enough time to finish your tasks

"Defer building until pain" means not building a feature until it is certain that a feature will be used. For example:

* Making a fake button, implementing its underlying features only after many (see [6](agile.md#6-use-data-to-make-decisions).) users have clicked on it
* Creating a small feature that doesn't work, implementing it only after people use it, using [exception-driven development](http://blog.codinghorror.com/exception-driven-development/) (see [6](agile.md#6-use-data-to-make-decisions).)

### What is the metric used to measure pain?

Whether some pain "sounds important" [sic] is the main metric used to measure and prioritise pain. (see [6](agile.md#6-use-data-to-make-decisions).)

### Always do the highest priority item

In a team, this is the task that is, assigned to you, with the highest priority value.

A high priority value indicates that the task is urgent (not important).

If two or more tasks have the same priority value, do them at the same time, which might eliminate dependency deadlocks (see [5](agile.md#5-avoid-task-dependencies).)

## "2. Deploy thin slices"

Instead of deploying a complete feature, deploy partial features. This will get a feature out to a customer as soon as possible, which helps detect bugs (see [6](agile.md#6-use-data-to-make-decisions).) early.

The following are examples of deploying thin slices:

* Deploying individual bug fixes

### Deploy often

As slices become thinner and thinner, continuous deployment can be easily achieved. At that point, code reviews will need to be done as soon as possible, typically approved or rejected in under an hour.

### Unknown unknowns

Deploying quickly and frequently helps identify, as often as you deploy, that a problem exists, or a hidden requirement is preventing a task from being done.

### Thin / Simple doesn't mean ugly

Writing code that borders "temporary" can have a negative result on the future velocity. 

While leaving magic numbers in that one/two places where they are used are acceptable, even thin slices require careful initial architectual consideration, because as a project increases in size, it gets more difficult to refactor.

As an example, if you were to design a skyscraper, you cannot deploy a wooden hut as your first thin slice, because none of the wooden hut is actually useful for finishing the skyscraper.

## "3. Use 3rd party tools"

If someone somewhere has made a tool that does what we want to do, then that tool shall be used until the tool no longer does what we want to do (e.g. we want more features). 

Even so, if said tool is open source, we will want to either fork or contribute to the same tool to meet our increasing requirements. This should be the last resort (see [1](agile.md#1-defer-building-until-pain).)

## "4. Architect Simply"

Put flexibility aside, because implementing flexibility vastly increases the complexity of the code, which conflicts with (4). 

Build exactly what is required of the task, and worry about the spaghetti code later.

### Keep old things around, or leave them for later?

History suggests that either can be done, depending on which one gets other features out to the customer faster. For example, architecting a brand-new development stack is considered beneficial, while redoing a bug-ridden feature is discouraged, because the feature already exists. 

However, redoing a complex feature is paradoxically encouraged, because this point (see [4](agile.md#4-architect-simply).) is axiomatically correct.

## "5. Avoid task dependencies"

Don't wait for things to start working on your task. 

There are two types of dependencies that can prevent you from working: internal and external dependencies.

### "3rd party" (external)

If you need to wait on a third party (e.g. another company) for action to be taken on their side of business, such as adding an API or a script tag, in order for you to finish your task, simply...

### "March ahead" (internal)

Work as if all dependencies exist. 

If an API does not exist, pretend it does, and work on. 

If you depend on a feature that does not exist, pretend the feature exists, and work on.

## "6. Use data to make decisions"

Never guess what features people use, what people want or don't want, or which bugs are more important to fix. Leverage analytics tools available to you (see [3](agile.md#3-use-3rd-party-tools).) to find out:

* What increases software performance
* What features users use most often
* A/B Testing
* Which bugs are most often hit by users

### Collect all data

Unless it takes too much time to collect the data (see [1](agile.md#1-defer-building-until-pain).)

#### Retrospectives

Agile development often involves formal [retrospectives](http://www.mountaingoatsoftware.com/agile/scrum/sprint-retrospective/) that helps identify what was done well last sprint, not done well, and things to continue doing.

## "7. Definition of Done"

In Kanban, there is a concept called "Plan - Do - Done", that divides all tasks into the three categories.

There are many occasions when you want to mark a task as done, but a task is only considered Done when the feature is deployed and tested.

If the feature turns out to be buggy, the task is still considered done. Just file another high priority task to fix that bug.

A checklist is available for determining whether your task is done:
* Code formatted
* Code commented
* Static code analysis passes
* All test cases pass
* Tested by yourself
* Code reviewed by other Developers
* Tested by QA
* Acceptance tested by Product Management
* Code merged into production repository.

### Deliverables

A task needs a list of deliverables ("what needed to be done" -- and "what got done?") and, preferably, a due date.

## Root Cause Analysis

If something goes wrong, ask [Five Whys](http://www.startuplessonslearned.com/2008/11/five-whys.html), whether or not it seems relevant, to drill down to the root cause.
Each why should follow with another why, so the answer becomes more and more fundamental.
The final Why should be answered with "how can it not happen again" as a retrospective.

>    why was the website down? The CPU utilization on all our front-end servers went to 100%
>    why did the CPU usage spike? A new bit of code contained an infinite loop!
>    why did that code get written? So-and-so made a mistake
>    why did his mistake get checked in? He didn't write a unit test for the feature
>    why didn't he write a unit test? He's a new employee, and he was not properly trained in TDD
>    die Endlösung: change the new engineer orientation to include TDD