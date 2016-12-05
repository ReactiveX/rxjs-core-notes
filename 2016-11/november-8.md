# November 8 ([discuss](https://github.com/ReactiveX/rxjs-core-notes/pull/4))

### Attendees

* [@kwonoj](https://github.com/kwonoj)
* [@blesh](https://github.com/blesh)
* [@mattpodwysocki](https://github.com/mattpodwysocki)
* [@jayphelps](https://github.com/jayphelps])

## TypeScript is forcing users to install types for chai, etc [#2112](https://github.com/ReactiveX/rxjs/issues/2112)

A TypeScript compiler bug is forcing RxJS TS users to install `chai` and any other dev dependency we use internally, when using the `@types` definitions. This is a known bug and fixed in [#11849](https://github.com/Microsoft/TypeScript/issues/11849) which should land in v2.1 of tsc.

#### Decisions

There is [a PR that solves this](https://github.com/ReactiveX/rxjs/pull/2113) by using the latest dev build of tsc, but we do not feel comfortable building an RxJS release with an unstable version of tsc.

We will try to get more insight into when v2.1 will be released with the fix upstream and if not within the next two weeks we will downgrade our type definition usage to use `@typings` instead of `@types`.

Users who want to work around this today can install the type definition for chai in their app:

```
npm install --save-dev @types/chai
```

## API docs are broken [#2111](https://github.com/ReactiveX/rxjs/issues/2111)

Our docs are broken due to two issues:

* We accidentally didn't build the CJS version during doc generation, which is currently used for esdocs
* Many of the JSDoc signatures were not placed next to the signatures themselves, which prevents ESDoc from picking them up correctly

#### Decisions

Andre's PR [#2118](https://github.com/ReactiveX/rxjs/pull/2118) looks good, needs final review, merge and republishing of docs.

## Dynamic operator invoking helper aka .operate() [#2036](https://github.com/ReactiveX/rxjs/pull/2036)

#### Decisions

Lack of type safety to any currently feasible solution makes this unattractive, even though existing solutions library authors use like `source.call(operator)` are unsafe as well.

No solid consensus yet, need more input from library authors whether this is truly desired or not. Punting for now.

## Internal: lint changes [#2104](https://github.com/ReactiveX/rxjs/pull/2104) [#2103](https://github.com/ReactiveX/rxjs/pull/2103)

Add several linting options to TSC compiler, instead of doing them at commit-time with tslint.

#### Decisions

* [#2104](https://github.com/ReactiveX/rxjs/pull/2104) `--noUnusedLocals` is not desirable for us currently, because it can disrupt debugging when sometimes you're commenting out things or temporarily have used code while you fix things. If we made it a warning only, we'd still need to use tslint to prevent it from being committed. We may reconsider later, but for now we'd like to keep the status quo.
* [#2103](https://github.com/ReactiveX/rxjs/pull/2103) `--noImplicitThis` adds value to certain places where it is indeed confusing what `this` currently is because of dynamic invocations, mostly around schedulers. We think this adds notable value while not significantly impeding debugging. Merge.

## Internal: random Yarn lockfile updates

Since switching to yarn for internal RxJS usage, we haven't yet experienced any performance wins and appear to have random lockfile changes when contributors `yarn install`.

Initial investigation into this suggests our travis config isn't correct to provide caching, which is likely fixable, but the lockfile random changes eludes us and so yarn is currently causing more problems than it's providing. tl;dr even though our package.json has `"typescript": "^2.0.6"` and our lockfile has `typescript@2.0.6`, doing a `yarn install` is bumping us up to `2.0.7` and updating the lockfile with this change. This seems counter to our understanding and initial discussions with James Kyle of yarn team suggests this isn't expected.

#### Decisions

Since we're very focused on shipping v5-final, and none of us are very confident in their understanding of how we're supposed to reliably use yarn, it was decided to switch back to using npm until a later date.

:shipit:
