### Agenda

- Monorepo: Do we start again from scratch with our build process? 
- Organization of code:
  - Move everything we don't want people using directly (Subscriber for example) to an `internal` directory?
  - Export locations for:
    - operators (e.g. `map`, `mergeAll`, etc)
    - static functions (e.g. `merge`, `race`, `concat`, `forkJoin`) - name collisions with operators?
    - observable creation methods: (e.g. `timer`, `range`, `fromEvent`) - are they much different than the static functions?
- Removal of secondary mappings from operators like `mergeMap`
- Rename `mergeMap` to `flatMap`? 
- Progress in docs effort (@ladyleet if she can attend)
- WHATWG Observable effort and alignment

## Attendees

[Ben Lesh](https://github.com/benlesh)
[Tracy Lee](https://github.com/ladyleet)

Brief discussion was had, but nothing important decided due to lack of attendance.
