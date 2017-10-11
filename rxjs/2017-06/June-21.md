# June 21st, 2017 ([discuss](https://github.com/ReactiveX/rxjs-core-notes/pull/10))

### Attendees

* [@blesh](https://github.com/blesh)
* [@kwonoj](https://github.com/kwonoj)
* [@david-driscoll](https://github.com/david-driscoll)

### Discussed

- Work is ongoing on lettable operators. We want to land that in 5.5 or 5.6 ahead of 6.0.
- Work is ongoing on reducing size of non-hotpath observables, again we want to land that in 5.5 or 5.6 ahead of 6.0
- OJ or David is going to drive an effort to clean up types exposed to the public for the 6.0 release. This will be a breaking change. The idea is to clean up the interfaces people see ahead of refactors around error handling, scheduling and other important efforts that likely will not land until version 7 or 8.
- Documentation is still an issue. Discussed trying to move documentation out of code files and into something more simplistic, like Markdown, in hopes of getting more contributions from the community.
