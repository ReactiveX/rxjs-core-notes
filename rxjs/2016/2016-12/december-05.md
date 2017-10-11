# December 5th, 2016 ([discuss](https://github.com/ReactiveX/rxjs-core-notes/pull/5))

### Attendees

* [@blesh](https://github.com/blesh)
* [@jayphelps](https://github.com/jayphelps])
* [@kwonoj](https://github.com/kwonoj)
* [@mattpodwysocki](https://github.com/mattpodwysocki)
* [@staltz](https://github.com/staltz])
* [@trxcllnt](https://github.com/trxcllnt])

## v5.0.0-final Timeline

Are we ready for v5.0.0-final? What are the blockers?

#### Decisions

We realize v5 has been in alpha/beta/rc for an unusually long amount of time. There are many reasons for this: v5 was a complete rewrite and as such we needed to shake out regressions, we changed the API in certain ways that we needed real-world feedback on to commit to, and in general there was a fear of locking into a major version would prevent us from releasing breaking changes that were necessary. In fact, v5 from a runtime stability prospective has been very _stable_ for almost a year. We have taken the learnings from this experience and unanimously agreed to start shipping major versions at a much more frequent interval to better signal true stability of both the code and the API surface.

We decided to ship v5.0.0-final one week from today, December 12th. We are in a code freeze, except for critical fixes that we all agree should ship for v5. The known list of those are these:

###### Blockers

* Typings for filter, find, first, last are incorrect, need to choose one of these: [#2170](https://github.com/ReactiveX/rxjs/pull/2170), [#2164](https://github.com/ReactiveX/rxjs/pull/2164)
* Customizing TimeoutError for `.timeout()` operator [is confusing](https://github.com/ReactiveX/rxjs/pull/2141), remove ability to customize the timeout message at all. Can revisit for v6 and beyond. Assigned: @blesh
* [Better error messages](https://github.com/ReactiveX/rxjs/pull/2152) for returning non-consumable objects/undefined/null in things like `mergeMap` projection. We all agree to merge. Assigned: @blesh
* Extending Observable still doesn't lift correctly in all cases, mostly static operators. Paul would like an opportunity to fix this before we ship, but we're on a tight schedule so it will depend on what he comes up with. Related: [#1876](https://github.com/ReactiveX/rxjs/issues/1876), [#1829](https://github.com/ReactiveX/rxjs/issues/1829). Assigned: @trxcllnt

## takeUntil does not stop taking when notifier complete()s [#2160](https://github.com/ReactiveX/rxjs/issues/2160)


```js
const onDestroy$: Subject<any> = new Subject();

Rx.Observable.interval()
    .takeUntil(onDestroy$)
    .subscribe(console.log, undefined, () => console.log("complete"));

setTimeout(() => {
    onDestroy$.complete();
    // doesn't cause the interval to stop. takeUntil only stops for `.next()`, not `.complete()`
}, 5000);
```

#### Decisions

This is as designed, and mirrors what Rx.NET and RxJS v4 did. Some believe it _should_ terminate when notifier complete()s (RxJava does), but we want to keep the status quo for now.

## Subscribing to multicast streams without an error handler can prevent subsequent subscribers from receiving errors [#2145](https://github.com/ReactiveX/rxjs/issues/2145)

```js

var observable = Rx.Observable.interval(200).do(function(i) {
  if (i === 2) {
    throw 'some error';
  }
}).share();

// This subscriber cares about errors and gets them
observable.subscribe(function(res) {
  console.log("first subscriber, next " + res);
}, function(err) {
  console.log("first subscriber, error " + err);
});

// This subscriber does not care about errors
observable.subscribe(function(res) {
  console.log("second subscriber, next " + res);
});

// This subscriber cares about errors, but never gets them
// because the second subscriber did not handle them
observable.subscribe(function(res) {
  console.log("third subscriber, next " + res);
}, function(err) {
  console.log("third subscriber, error " + err);
});
```

#### Decisions

This is the same behavior as v4. This exact topic is already being considered by TC39 for the [Observable spec](https://github.com/tc39/proposal-observable) because of DOM event handler streams are multicast.

Instead of guessing what TC39 might decide, we're going to keep the status quo because v4 handles it this way as well and the solutions are rather involved and highly likely we'll not align with the TC39. We should have a better idea of what TC39 wants to do soon.

:shipit:
