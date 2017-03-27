## Attendees

@benlesh @kwonoj


### Splitting DOM Observables off

- @benlesh discussed possibly splitting the Http/AJAX observable stuff out of Angular/http 
  and using it as the official HTTP/AJAX implementation for RxJS and Angular as well.
  Needs follow up with @robwormald and @igorminar
 
### Zones

- Still need benchmarks around each approach. Once we have the numbers, we can merge one of the methods of adding Zones

### Pipe PR

- No real opinion. Lose type inference

### Next major release

- Want to only introduce one or two small breaking changes at a time, possibly on a two month cadence.
- Need to align with major customers like Angular.
  
### Publishing ES6 Module

- Angular team needs this.
- Can we reuse the ES6 build that exists for the doc gen?
- Can we ship both inside of CJS modules directories: @benlesh and @kwonoj are opposed to this idea.
  - This will hurt Electron users.
  - the `@reactivex/rxjs` build has all possible builds in it, so we don't really need to ship this with `rxjs`
  - Some people don't want to change to `@reactivex/rxjs` to use the ES6 modules, tho.
 
### Removal of Error rethrowing

- To align with TC39 proposal
- To prevent producer interference
- Pass the error to some global handler of some sort. (Similar to promise unhandled error)

### PR Merging strategy

- If 2 approvals from core team, and it's a "next patch" version, merge it.
- If it's minor or major do not merge it right away.
- Docs changes can be merged right away.
