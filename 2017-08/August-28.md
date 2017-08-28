# August 28nd, 2017 ([discuss](https://github.com/ReactiveX/rxjs-core-notes/pull/11))

### Attendees

* [@benlesh](https://github.com/benlesh)
* [@ladyleet](https://github.com/ladyleet)
* [@kwonoj](https://github.com/kwonoj)
* [@david-driscoll](https://github.com/david-driscoll)

### Discussed

* @ladyleet and @david-driscoll discovered that they are neighbors.
* @ladyleet has whiskey at her house
* @benlesh should stop goofing around

 
* How can we help people publish their own operators and features?
* Should we have a userland GitHub organization?
  - Maybe use @reactivex
  - for user-land projects related to RxJS
  - mostly for custom operators and features
  - also for tooling
  - For custom operators and features we should provide a custom repository people can fork
  - Must have a clear code-of-conduct
  - What is the criteria to even get a repository in this org?
  - Electron does something like this (Electron-Userland)
  - examples
    - https://github.com/cake-contrib
    - https://github.com/electron-userland/
  - Governence would be hard: Consistency, Code quality, Code of Conduct, etc.
   
 * Mono-repo - many packages: @david-driscoll foolishly throws himself on the sword. This could be the real solution to the userland packages
 
 
 * Lettables - Jason Aden from Google's Angular Team is helping port operators to lettable operators... should be out in 5.5.0
 
 * ES Module publish - Jason Aden https://github.com/ReactiveX/rxjs/pull/2804
 
 The idea is to publish .esm files in an adjacent tree along with appropriate package.json files. This is "in addition to" the current `rxjs` publish, not along-side or instead-of.
 
 
 * Documentation effort
   - Tracy has a list of ~27 people that want to contribute.
   - Documentation
     - API docs
     - Examples
     - Tutorials
     - General information
     - Build/bundling basics
     - working with frameworks
   - Number one complaint has been lack of solid examples.
   - Brian Truncone's project. He's willing to contribute the content from his site to our documentation. (https://github.com/btroncone/learn-rxjs)
   
   1. General Information Site
   2. Form the Learning Team
   3. Create Issues so people can start contributing
     - Add a label for issues
   4. Link beta docs from current docs until current docs are more complete
   5. Find example docs we think are useful (Angular docs, React?, LoDash docs, MDN)
 
 
