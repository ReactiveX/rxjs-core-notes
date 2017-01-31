# January 30th, 2017 ([discuss](https://github.com/ReactiveX/rxjs-core-notes/pull/8))

### Attendees

* [@blesh](https://github.com/blesh)
* [@david-driscoll](https://github.com/david-driscoll)
* [@jayphelps](https://github.com/jayphelps)
* [@kwonoj](https://github.com/kwonoj)
* [@mattpodwysocki](https://github.com/mattpodwysocki)
* [@staltz](https://github.com/staltz)

## TS 2.1 custom Error objects [#2190](https://github.com/ReactiveX/rxjs/pull/2190)

TypeScript 2.1 changed transpiled output in way that makes extending the native `Error` object no longer work. We have a proposed solution, but mostly untested.

#### Decisions

Punt and work with ng2 team towards the same solution, since they have the problem too.

## Inject tslib functions [#2121](https://github.com/ReactiveX/rxjs/pull/2121)

We don't currently have anything that outright tests that our global UMD build works as expected--this is actually mostly the normal in OSS, very few projects that publish global builds actually test those builds themselves in an automated fashion, they usually run their tests against their CJS or ES modules.

That said, merging this wouldn't change that fact and we can try the build by hand before we publish.

#### Decisions

Merge.

## fix(buffer): Emit last buffer if source completes [#2174](https://github.com/ReactiveX/rxjs/pull/2174)

#### Decisions

Looks good, but even though we didn't intend for the existing behavior, since we shipped it people could be relying on it.

Merge into next major release, not minor because it is a BREAKING CHANGE.

## feat(windowTime): maxWindowSize parameter in windowTime operator [#2187](https://github.com/ReactiveX/rxjs/pull/2187)

#### Decisions

@jayphelps will fix reentry issues, then we can merge into master.

## fix(buffer): subscribe to source and closingNotifier in proper order [#2195](https://github.com/ReactiveX/rxjs/pull/2195)

#### Decisions

Needs another review, is BREAKING ChANGE, so would be major version


## feat(takeUntil): change behavior of takeUntil to not subscribe to source if notifier is synchronous [#2189](https://github.com/ReactiveX/rxjs/pull/2189)

This one is hotly debated. It's one of those that could go either way depending on your use case. This would be a breaking change, so major version. All of the arguments discussed were rehashes of the discussion in the PR thread.

#### Decisions

If most of us don't agree on it, we don't want to make the change. @trxcllnt, the PR author and core team member, was not in attendance so we want to give him an opportunity to champion the argument further at a future meeting.

## test(filter): enable type inference to marble diagram [#2202](https://github.com/ReactiveX/rxjs/pull/2202)

While the solution itself isn't ideal, we're mostly OK with it since no other viable solution is known. There is concern that we will forget about it and remove/reformat the lines later and unknowingly break it.

#### Decisions

OJ will look into some way to detect/prevent us from later accidentally removing/reformatting these import lines.

## .op() helper [#2034](https://github.com/ReactiveX/rxjs/pull/2034)

Generally everyone agreed we need something like this. There was a debate about whether or not we could have the `.let()` operator imported by default and just have people use that:

```js
source
  .let(s => filter.call(s, x => x > 1))
  .let(s => map.call(s, x => x + 10))

// vs.

source
  .op(filter, x => x > 1)
  .op(map, x => x + 10)
```

`.let()` does not have operator type safety, whereas we _can_ add safety for `.op()` (thought the PR doesn't currently have the overload signatures yet)

#### Decisions

We think the terseness of `.op()` combined with the planned type safety additions are enough to justify adding.

@jayphelps will add type signature overloads for all operator patching files, so that `.op()` is type-safe. When that's ready, we'll merge.

## feat(Zone): add support for Zone.js [#2266](https://github.com/ReactiveX/rxjs/pull/2266)

This isn't really _support_ for Zones, it's more adding a different behavior about what zone you subscribe in vs. declare your observable chain in. The problem and justifications are quite complex, see the ticket for full details.

All of us would prefer it if we could provide a patching module, e.g. `rxjs/add/zones` that would monkey patch the necessary changes instead of baking them in by default.

#### Decisions

We need to test the performance difference between the three:

* Current (no extra zones stuff)
* Using monkey patching (`rxjs/add/zones`)
* Merged into core itself

Need to continue working closely with the Angular team.

## Template for creating new operators [#2299](https://github.com/ReactiveX/rxjs/issues/2299)

Adding new operators to core is not a trivial process. There's a ton of bikeshedding that needs to go on, and for good reasons. We want to make that process more clear and have the discussions early on before wasted code is written.

#### Decisions

@mattpodwysocki will create the initial document

:shipit:
