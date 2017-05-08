# March 29th, 2017 ([discuss](https://github.com/ReactiveX/rxjs-core-notes/pull/8))

### Attendees

* [@blesh](https://github.com/blesh)
* [@kwonoj](https://github.com/kwonoj)
* [@david-driscoll](https://github.com/david-driscoll)


## Moving Toward Lettable Operators

The idea here is to update RxJS 5 to include all operators as higher-order functions that return a lettable function. For example:  `const map = (fn) => (source$) => currentMapFn.call(source$, fn)` (this is the most primitive implementation)

### Pros

 - Much more flexible overall
 - No more prototype augmentation for those that opt to use this method
 - Better tree shaking
 
### Cons

 - TypeScript does not infer types through this sort of chaining.
 - Yet another way for people to use RxJS

The outcome here is that @benlesh will talk to folks at Google (who really want this) and reach out to the TypeScript team to see if we can't get this resolved on the TypeScript side.

### Unifying AJAX: Both Angular and RxJS have an Observable-based implementation of AJAX, we should unify those into one framework-agnostic implementation

Ideally this will reduce confusion for Angular users. Also it should result in a better maintained AJAX implementation. Currently, not many people use the Rx implementation because of poor documentation.

Perhaps we can also move the `WebSocketSubject` to a nuetral space and make it easier to use with Angular.

@benlesh will work with the Angular team to see what we can work out.

### Outstanding Bugs/Issues

Due to low headcount/availabilty we're getting backed up on issues and PRs in the repo. This is also in part due to not having a solid unified direction for where we want to go with certain parts of the library.

We need to come up with a solid direction, and that will help guide whether or not we need to close certain issues or PRs that are currently in limbo because we're undecided.

Current direction is that we want to aim for reducing the size of Rx's footprint, move to lettable operators, and refactor the `TestScheduler` to make it easier for users to consume.

### T-Rx

@benlesh showed off work on a private prototype of RxJS that weighs in at around 3k minified and gzipped. It has most if not all updates in it that we want to introduce to RxJS over the long term. This will remain in a private repository for now, as it's far too alpha for anyone to be using.

One thought is that once it's ready to be alpha'd properly (we have current tests passing on it) we can move it over to a branch on the RxJS main repository, and start some concurrent development between it and current Rx. Another approach would be to try to steer the current repository in that direction, however that would involve a few moments of extremely difficult refactors, mostly around schedulers and the like. Final strategy TBD.

