# Meeting Notes January 31, 2018

## Attendees

[Ben Lesh](https://github.com/benlesh)
[OJ Kwon](https://github.com/kwonoj)
[David Driscoll](http://github.com/david-driscoll)
[Tracy Lee](http://github.com/ladyleet)
[Ashwin Sureshkumar](http://github.com/ashwin-sureshkumar)


## Discussed

* Moving RxSandbox into Rx proper - OJ created a proof of concept. Once we agree with it it can be ported over to RxJS core.
  * Start an issue of what we want to change about test scheduling.
    * Need to go through all the things we can fix in the TestScheduler work and get aligned.
    * PR # tracking is #3266.
    * Jay had some ideas about fixing the TestScheduler as well that we need to align on.
    * Lots of discussion around test scheduler - separate meeting to be scheduled next week to discuss this specifically with Jay, Ben, OJ.
  
* Ben has been going through issues and closing them out.
  * Could use help from others to even label the issues so we know someone has looked at the issues.

* David's PR #3265
  * Goes through and updates our tests and imports tests instead of having them global & brings in better typing, etc.
  * David needs to fix the build! Ben and OJ to review after.

* Monorepo
  * The angular folks may or may not take this over.
  * Ben to ping Igor Minar and Jason Aiden about this.

* Async iterable support
  * Ben has been creating able to create observable from async iterable. 
  * Implementing async iterable on observable - still thinking about whether we should do this or not - lots of bikeshedding needed.
  * Should we implement a toAsync iterable first for async iterable support - do this first vs the first two above.
  * No PRs have been submitted yet.

* Conversation around removing all polyfills from RxJS completely PR #3263
  * Responsibility should be for the person that needs the polyfill so we reduce bloat of our library - this is in V6 in master.
  * Other core team members can work on this - work should be easy.
  
* Discussed other PRs
  * 

* Learning team meeting update
  * Update from Tracy - Jan 31 was the last meeting.
