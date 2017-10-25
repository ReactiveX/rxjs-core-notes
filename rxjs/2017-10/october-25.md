# October 25th, 2017

### Attendees

* [@benlesh](https://github.com/benlesh)
* [@ladyleet](https://github.com/ladyleet)
* [@kwonoj](https://github.com/kwonoj)

### Discussed

- SystemJS folks still having issues, but have always had issues.
  - Can we continue to support them? 
- Mono Repo discussion: What we want to do is have a top level lerna (or something) that can build/publish more than one package under a modules directory. One of the things we'd like is to move the patching operators (`rxjs/add/*` to a separate package like `rxjs-dotchaining` or the like)
- Talk Nightlies: @kwonoj is going to work on getting Nightlies going. No changelogs will be generated for nightlies, because there would be too much flux in them.
- Open Collective: @benlesh signed us up for OC, however, we need to figure out more about how it works and more importantly, what we would do with the money. Both @benlesh and @kwonoj expressed concern that the introduction of money could bring politics and feelings into play in the repo/community.
- Discussion around inviting non-core team members to core team meetings: The core team meetings are for private discussion of RxJS issues/direction/concerns, and while we may invite non-core team members for specific reasons from time to time, it should really be for core team members only unless otherwise needed.
- Remove secondary map: Discussed removing secondary mapping selector from operators like `mergeMap`, `switchMap`, `concatMap`: @kwonoj and @benlesh generally in favor, but @kwonoj is worried about introducing too many breaking changes in v6. So we want to do it, but whether or not it's in v6 is TBD.
- deprecate `@reactivex/rxjs` and `rxjs-es6` and only publish `rxjs` :+1: - This is definitely happening before v6.
- move add/ operators to a separate package in monorepo - This is something we'd like for v6. So we aren't dropping support for the patching operators, rather just moving them to another package: This is for a few reasons: 1) we'd like to encourage people ot use the functional operators. 2) It'll reduce the size of the package for people using Node or Electron. 3) It will reduce confusion when using the library
- Scheduler discussion: Discussion around [The Future Of Schedulers](https://github.com/ReactiveX/rxjs/issues/2935) issue. Both @kwonoj and @benlesh agree we should reduce the size impact of schedulers on the library. @kwonoj is concerned about the number of breaking changes for v6, so we'll need to plan it out, but it can be seen that there is perhaps a little too much code/engineering around scheduling within the library, and we can definitely reduce the size of the library by taking a smarter approach with schedulers. This is to be discussed more in the future, no solid decisions made.
