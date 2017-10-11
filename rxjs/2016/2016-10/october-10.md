# October 10 ([discuss](https://github.com/ReactiveX/rxjs-core-notes/pull/1))

## v5 RC1

* Are we ready?
* What's blocking?

#### Decisions

Need to remove `.cache()` operator because it tried to solve everyone's usecases without solving any of them. Need to stop publishing `rxjs-es` and not include ES6 builds in `@reactivex/rxjs`.

Update: v5.0.0-rc1 was released!


## Official stance/process on adding new operators [#1950](https://github.com/ReactiveX/rxjs/pull/1950) [#1928](https://github.com/ReactiveX/rxjs/pull/1928)

* Should we make a "kitchen sink" addon?
* Should we slim down existing operators even further? 
* Is this a filesize problem, a documentation presentation problem, both?

#### Decisions

A large chunk of our users don't use operator patching; some for technical reasons and others out of convenience. We want to have the core RxJS you `import Rx from 'rxjs';` be small--smaller than it is today even. That means removing some operators like possibly `.every()`, `.reduce()`, etc. Keep the core limited to operators which are very common (like `.map()`) or fairly common and non-trivial to implement for Rx beginners.

However, there are many operators that people would like, even if their usage isn't as common. We want to have some answer to this, likely involving some form of addons. One way is to put them all into "kitchen-sink" addon. There are concerns around bloating node_modules file size for Electron users who commonly don't do operator patching or even bundling.

For now, the status quo will be that we'll not be accepting any new operators for v5, at least as a general rule. Before v5.0.0-final, we may remove some operators we feel do not belong in core and bring them back in some future addon. If we do remove any, we will now try to include a code snippet in the CHANGELOG showing how you can easily recreate the same behavior.

We want to focus as much as possible on shipping a stable v5.0.0-final ASAP, which means keeping our limited resources as undivided as possible. If you're interested in spearheading the kitchen-sink/addon effort now, please reach out.

## Productizing the TestScheduler [#1775](https://github.com/ReactiveX/rxjs/issues/1775)

* reducing boilerplate for creating TestScheduler instance w/ helpers like `createHotObservable()` because verbose vs just `hot()`
* Automatically injecting the TestScheduler into pre-existing observable chains. e.g. `delay(1000)` ideally shouldn't require the user to write injection logic.
* How we do we let users provide their equality checking logic from their test runner?
* Is this worth blocking a v5 release?

#### Decisions

Mocking `AsapScheduler` with `TestScheduler` would produce different behavior in some cases. Very few people use schedulers other than when the `AsyncScheduler` is implicitly added by default for time-based operators. We need to do more experimenting and discussing if it's feasible to have a test scheduler that keeps the behavior of the scheduler it's mocking, except controlling virtual time. e.g. `AsapScheduler`, `AnimationFrameScheduler`, `QueueScheduler`.

Still create `TestScheduler.run(({ cold, hot }) => {})` helper which creates instance, injects scheduler to mock `AsyncScheduler` and additional boilerplate.

This work will likely collide with work @blesh is doing with refactoring some error handling out of operators and into the schedulers.

Assigned: @jayphelps

## Stop publishing rxjs-es. Move ES6 build to output .mjs files alongside the CJS .js files. [#1671](https://github.com/ReactiveX/rxjs/issues/1671)
# ES5 code w/ ES Modules [#1925](https://github.com/ReactiveX/rxjs/issues/1925)

I don't believe we're still planning to do .mjs files, not sure what the .mjs status is in the node community. 

Side note, if we stop building pure ES6, there has been some community concern we won't be publishing ES6 code on the documentation website http://reactivex.io/rxjs/source.html which is easier to read cause it doesn't have all the TypeScript generics and such.

#### Decisions

Stop publishing rxjs-es and any ES6 or ES Module builds at all. Focus efforts on shipping 5.0.0-final and then we can add ES Module builds later, since additive things are not breaking changes.

Continue building ES6 code for ESDocs generation only--that means users will not ever be able to depend on this, it's simply because there is no good TypeScript equivalent for ESDoc at the moment.

Assigned: @blesh

## Adopting TypeScript 2.0 [#1968](https://github.com/ReactiveX/rxjs/pull/1968) [#1978](https://github.com/ReactiveX/rxjs/pull/1978)

* When should we adopt?
* Expected backlash?
* Would allow us to do ES5 code w/ ES Modules [#1925](https://github.com/ReactiveX/rxjs/issues/1925) [#1671](https://github.com/ReactiveX/rxjs/issues/1671) in the future

#### Decisions

Confirmed, we have upgrade to TypeScript 2.0. Angular2 users by far make up a majority of our TypeScript userbase and the trend is a quick migration to 2.0.


## Operators that are reserved words requiring _underscore convention [#1958](https://github.com/ReactiveX/rxjs/issues/1958)

Some operator names are reserved words, which require us to prefix them with an _underscore so that they can be imported directly. Should we rename them or is the _underscore pattern acceptable? How are we currently documenting these exceptional uses?

  * catch
  * switch
  * do
  * finally
  * let
  * throw

#### Decisions

Leave unchanged for v5, revisit for in the future v6, etc. based on more user feedback.

## Publishing meeting notes

* Is this something we should do?
* Who will record and publish them?
* What process to add agenda items?

#### Decisions

Let's do it! (obviously, you're reading this)

If you have something to add for the agenda, for now, just bug @jayphelps. We're going to shake out this process for a couple iterations to figure out what works.

Assigned: @jayphelps

:shipit:
