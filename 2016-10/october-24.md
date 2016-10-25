# October 24 ([discuss](https://github.com/ReactiveX/rxjs-core-notes/pull/2))

## Attendees

* @kwonoj
* @blesh
* @jayphelps

## Outstanding PRs

* [#2025](https://github.com/ReactiveX/rxjs/pull/2025), [#2039](https://github.com/ReactiveX/rxjs/pull/2039), [#2042](https://github.com/ReactiveX/rxjs/pull/2042), [#2046](https://github.com/ReactiveX/rxjs/pull/2046), [#2050](https://github.com/ReactiveX/rxjs/pull/2050)
  * Merge them. Assigned @jayphelps
* [#2049](https://github.com/ReactiveX/rxjs/pull/2049)
  * Needs updated jsdocs to no longer reference `compare` argument. Assigned @blesh
* [#1950](https://github.com/ReactiveX/rxjs/pull/1950), [#2051](https://github.com/ReactiveX/rxjs/pull/2051)
  * `.some()` and `.toSet()` operators. We don't believe these belong in core at this time. We will continue to consider removing `.every()`, `.reduce()`, and maybe others from core--possibly move them into an addon at a later date. More info about our thoughts on adding new operators [found here](https://github.com/ReactiveX/rxjs-core-notes/blob/32ea3f8e3488c38b4498492ba442efaf93667c7a/2016-10/october-10.md#official-stanceprocess-on-adding-new-operators-1950-1928). We want to focus on shipping v5.0.0-final ASAP for now. Will investigate how common these other similar operators are used in real world code to inform our decision on whether to remove them or not.
  * Discuss with PR owners if they'd like to keep the PRs open until then and/or help with the efforts to support some form of kitchen-sink addon--possibly still included in the `rxjs` npm module, but not imported by default. Assigned: @jayphelps
* [#2057](https://github.com/ReactiveX/rxjs/pull/2057)
  * We absolutely need a more clear MIGRATION guide that also provides solutions to operators that existed in v4 but not v5. Assigned: @jayphelps, help wanted too.
* [#2024](https://github.com/ReactiveX/rxjs/pull/2024)
  * We don't have consensus on the linting preferences this PR imposes. We agreed to keep the status quo for now. There are also possible concerns about this actually increasing inconsistency between public and private function parameters.
* [#1852](https://github.com/ReactiveX/rxjs/pull/1852)
  * We think adding a `removeEventListener()` mock to [.markdown-doctest-setup.js](https://github.com/ReactiveX/rxjs/blob/fee7585b4d2ed786065a40e580b862bfd9211281/.markdown-doctest-setup.js#L26) will let the testing of the markdown examples correctly pass. Need to sync up with PR owner to suggest solution. Assigned @jayphelps

:shipit:
