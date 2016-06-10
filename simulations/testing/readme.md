You didn't think you were done just by writing the mungebit function did you?

Hopefully you verified your mungebit works.  But it's preferable to be able to verify this in a systematic and ongoing basis so future developers don't have to manually run dozens of mungebits to ensure their accuracy.  How do we do this
Glad you asked! ... Synergy. Errr Testing! 

Code that is easily testable is often well structured and well written code and therefore we will have you write some tests for your custom mungebit. 

## Learning

* [Understand the philosophy of automated tests](https://medium.com/javascript-scene/what-every-unit-test-needs-f6cd34d9836d#.gvu7uqszv)
* [Testing in R](http://r-pkgs.had.co.nz/tests.html)
* [How we test within Avant Analytics](https://github.com/avantcredit/avant-analytics/tree/master/test/README.md)
* **Optional:** Learn about [R CMD CHECK](http://r-pkgs.had.co.nz/check.html), which tests for other things that can go wrong in a package, in addition to automated test failures.
* **Optional:** Learn about [verifications and quickcheck](https://github.com/peterhurford/checkr/blob/master/README.md).

## Exercises

1. Add some tests to your mean imputation package to make sure that it (a) successfully imputes one NA, that it (b) successfully imputes 2+ NAs, (c) that it works if there are no NAs, and (d) that it works if there are all NAs.

2. Write at least three tests for your custom mungebit. Append The DS checklist to PR and check relavant boxes.

3. **Optional:** Quickcheck your imputation function in your package.

4. **Optional:** Quickcheck your custom mungebit.
