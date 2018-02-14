# Meeting Notes January 31, 2018

## Attendees

[Ben Lesh](https://github.com/benlesh)
[OJ Kwon](https://github.com/kwonoj)
[David Driscoll](http://github.com/david-driscoll)
[Tracy Lee](http://github.com/ladyleet)
[Ashwin Sureshkumar](http://github.com/ashwin-sureshkumar)

## Discussed

* Jay’s issue 3227 - unable to come up with solution around ESM module imports and tree shaking right now.

* OJ Migrating new TestScheduler PR into v6 core #3314
  * Have Jay review since he is also looking to work on some TestScheduler changes soon.
  * Jay and Ben has been bikeshedding on this too.
  * Review at next core meeting and discuss on github.

* Review David Driscoll's PR #3265
  * Updating test helpers to be strongly typed.
  * Ben and OJ :shipit: and merged.

* Ben: Operators that have child subscriptions like mergeMap are currently hanging on to the source subscription longer than it should and tests reflect it.
  * Need to fix before 6 goes out because it's a breaking change.

* Change to remove result selectors needs to happen #3304

* Deprecation strategy
  * Need to general strategy to have migration plan for users.
  * Will be interesting to see feedback from V5 to V6 to decide on how we handle this in the future.

* Async subscription comments from fetch polyfill guys about async teardown (issue #2758)

* Monorepo proposal from Bazel
  * Google has been committed to do this but there has been no progress.
  * Ben to ping people about this.
  * See where progress is on 3/1.