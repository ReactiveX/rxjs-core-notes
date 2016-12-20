# December 20th, 2016 ([discuss](https://github.com/ReactiveX/rxjs-core-notes/pull/6))

### Attendees

* [@blesh](https://github.com/blesh)
* [@jayphelps](https://github.com/jayphelps])
* [@mattpodwysocki](https://github.com/mattpodwysocki)

## Branching Strategy

We originally were thinking of having three branches: **master**, **minor**, **patch**, but after discussing decided on two branches: **master** and **next**

- **master: anything that can be released in a minor/patch bump, but no breaking changes. Most PRs will be merged into here.
- **next**: everything from **master** (except incompatible changes) and breaking changes or major rewrites. This branch tracks the next major release, e.g. 6.0. We will manually rebase **master** into here, before every breaking change PR merge.

## VirtualTimeScheduler API additions

@mattpodwysocki would like to add the ability to manually control the passing of relative time with the VirtualTimeScheduler, similar to RxJS v4 was able to do. e.g. `scheduler.advanceBy(2000)`

#### Decisions

@mattpodwysocki will champion a proposal in collaboration with @trxcllnt.

## Error trapping

In cases of multicast, lack of error trapping can cause very undesired behavior for users when a synchronous observer fails. Error trapping is the proposed solution, and the [same behavior that Promises have](https://developer.mozilla.org/en-US/docs/Mozilla/JavaScript_code_modules/Promise.jsm/Examples#The_case_of_unhandled_rejections)--exceptions in one observer do not prevent other observers from receiving synchronous values. This is being discussed in TC39 Observable spec and the word on the street is that native Observables will likely ship _with_ error trapping. For Observables, it becomes even more important that Promises because of the plans for browsers to support observable event listeners--similar to `Observable.fromEvent(el, 'name')` is multicast, so errors in one subscribers should not prevent any others from receiving them!

Just like with Promises, this is a hot topic of debate because using error trapping means that the exception is "silently swallowed" from the normal propagation of JS exceptions--however, the HTML spec added an `unhandledrejection` event on the `window` object that can be used to listen for and report swallowed errors. Google Chrome still reports these errors in the console, to aid in debugging.

This is a rather confusing problem, so don't be surprised if it seems unclear (or even stupid why we would want this). For a better understanding, see existing discussions on Promise unhandled rejections in the community at large aka Google.

#### Decisions

We will continue to receive guidance from TC39, but we feel strongly they will move to adopt error trapping (like Promises) so we may look to changing this for v6 or v7. We would still provide a similar mechanism to `unhandledrejection` events as well as still still having the error show up in the console for debugging.

# Documentation

Anyone have suggested strategies to bring it all up to date and keep it that way?

#### Decisions

We will commit to enforcing that any new features must be documented. To entice contributors to document existing APIs will be considering some rewards.

# Review PRs/Issues

* We're looking into adding static versions of mergeAll/concatAll/etc operators
* Fix groupBy to dispose of outer subscription [#2201](https://github.com/ReactiveX/rxjs/pull/2201)
  * We're not confident to merge this without a test. Assigned: @blesh
* Add join/groupJoin operators [#2194](https://github.com/ReactiveX/rxjs/pull/2194)
  * Aren't frequently used, but are hard to implement for users. Growing number of node.js users of RxJS means we would like to include them but want to release them together.
* Cancel scheduled timeout work, if no longer needed [#2135](https://github.com/ReactiveX/rxjs/pull/2135)
	* Needs comments on why we're using lift this way, also remove npm script changes. Assigned: @jayphelps

:shipit:
