# November 29, 2017 Docs Meeting

### Attendees

* [@ladyleet](http://github.com/ladyleet)
* [@benlesh](http://github.com/benlesh)
* [@kwonoj](http://github.com/kwonoj)
* [@btroncone](http://github.com/btroncone)
* [@only1mranderson](http://github.com/only1mranderson)
* [@ashwin-sureshkumar](http://github.com/ashwin-sureshkumar)
* [@necoline](http://github.com/necoline)
* [@knittingcodemonkey](http://github.com/knittingcodemonkey)
* [@mustafamg](http://github.com/mustafamg)
* [@valorkin](http://github.com/valorkin)

### Items Discussed

* Open PRs
  * Everyone has been really active in code reviews and merging PRs, so there are no outstanding ones that need attention!

* Companies Page
  * Andrew Anderson's PR on the company page is just about complete. Discussion on best way to host data and what to do about firebase credentials
  * Decision - ad hoc for now until it grows and we decide we need to figure something new out.

* Translations
  * Dmitriy Shekhovtsov spent a bit of time talking through what he feels like we need to do to optimize translations. 
  * Conclusion: No objections to use ngx-translate and continue down the pending PR with translations.

* Documentation issues - current docs vs new docs - how to handle?
  * Decision: Ad-hoc for now since the # of requests is low. As people create issues on the rxjs repo, Tracy Lee will triage and create issues on rxjs docs or help redirect.

* Beta launch of site
  * Goal is to launch so people feel like they are able to contribute easier and can see the fruits of their labor.
  * Brian mentioned there are only about 20% of operators currently documented.
  * Decision is that we should not wait until mobile optimization before launch, though it is something we need to address.
  * 2 items before launch
    * Create a header that explicitly says these docs are beta.
    * Have Jen Luker go over the site once again and make sure it is a11y friendly.
  * What beta domain do we put it on? 
    * Can be stand alone for now 
    * Can either be github pages or firebase

* Versioning
  * Ashwin Sureshkumar brought this up as it is being discussed on github.
  * Ashwin to come up with a proposal by next meeting and work with Dmitriy since he has experience doing versioning with ngx-bootstrap.

* Before final launch of site
  * All operators need to be documented
  * Jay Phelps's PR related to getting docs out of source code needs to be worked on and merged somehow
  * Link to source code needs and docs in source code
  * Reconciliation of documentation
  * Review and approval of all descriptions, etc from core team
  * Getting started guide

* Mobile Issues
  * JSBin not loading properly on mobile
  * RxMarbles graphs not pretty on mobile

* Other Notes
  * Please promote the RxJS docs site on social channels so we can get more people contributing to the docs! 
  * Andrew Anderson said he would work on the companies page.

* Action Items
  * Tracy to discuss beta launch of site with others
  * Getting ngx-translate to a place of launch 
