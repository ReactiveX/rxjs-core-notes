# Meeting Notes August 1, 2018

## Attendees

* [Tracy Lee](http://github.com/ladyleet)
* [Ben Lesh](http://github.com/benlesh)
* [Nicholas Jamieson](http://github.com/cartant)
* [Paul Taylor](http://github.com/trxcllnt)
* [David Driscoll](http://github.com/david-driscoll)

## Discussed

- [`forEach` PR](https://github.com/ReactiveX/rxjs/pull/3977): Adding a secondary "Subscription as a cancellation token" argument to `forEach`. Concensus was a "thumbs up".
- Making Observable "awaitable". @david-driscoll brought up the desire to make Observable thennable, and therefor awaitable. Everyone agreed that it's problematic to do so, because people will not be expecting multiple side effects when awaiting the observable twice (in comparision to promises)
- [Splitting publish, multicast etc](https://github.com/reactivex/rxjs/issues/3833). Thumbs up from everyone. The idea here is to split the publish operator into a static `publish`/`multicast` that returns `ConnectableObservable<T>`, and an operator like `publishWith` or `publishAs` that must have the `selector`/`projection` argument and returns `Observable<T>`.
- [xWith operators](https://github.com/reactivex/rxjs/issues/3927): Thumbs up from everyone. The idea here is instead of just deprecating the `concat`, `zip`, et al _operators_, we rename them (alias them but still deprecate the old names) to `concatWith`, `zipWith`, et al.
- [Possibly removing instanceof checks from the library](https://github.com/reactivex/rxjs/issues/3828): Thumbs down. Status quo maintained. Given the performance impact of removing `instanceof` checks in favor of property assertions in potentially hot path areas like inner subscriptions, it was decided to leave the `instanceof` checks in place.
- Interop with Node Streams - @trxcllnt brought up the desire to convert an Observable to a Node Stream. This has a lot of implications around needing to provide various buffering strategies. It was decided that it might be better to provide conversion to **Async Iterator**, which is more easily converted to a Node Stream, and is likely more desireable. Still, the buffering strategy is an issue to be resolved. @trxcllnt said he may look into coming out with a design document for this in the future.
