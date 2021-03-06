# Submission notes

## Purpose

- Fixed problem wherein reading the CITATION file fails with package ‘quanteda’ not found when package is not installed.  

- Fixed this problem:
    > You have examples for unexported function "friendly_class_undefined_message" in friendly_class_undefined_message.Rd.
    > Please either add quanteda::: to the function calls in the examples or omit these examples or export these functions.
    
- Added more contributors to DESCRIPTION, in response to a request from Swetlana Herbrandt.  We did not add either "Dáil Éireann Debate" or Meik Michalke, however.  The first is a source, and we have now documented that better in the data object it comes from.  The second is a package whose manual we cite, but who did not contribute any code and whose code was not used or modified in our package.  

- Added numerous other packages used only in unit tests to `Suggests:`, following an email note from Kurt Hornik.

- Bug fixes and stability enhancements.  

- Improvements to documentation.  

- Some feature additions.  

- On UBSAN issues, please see below.
 
## Test environments

* local macOS 10.13.4 install, R 3.4.4
* ubuntu Ubuntu 14.04.5 LTS (on travis-ci), R 3.4.4
* Windows Server 2012 R2 x64 (build 9600), R 3.4.4 (on Appveyor)
* local Windows 10, R 3.4.4
* win-builder (devel and release)

## R CMD check results

### Note on UBSAN issues

Our package has some recurring UBSAN issues.  These are warnings that occur in RcppParallel, because of code in the TBB (Intel Threading Building Blocks) library used by RcppParallel.  We have been in a wide discussion with the RcppParallel development team (see https://github.com/RcppCore/RcppParallel/issues/36) but they have identified the problem as an object call in TBB.  This seems to have no consequences for stability in packages that use these functions.  One of the RcppParallel developers, Kevin Ushey (kevinushey@gmail.com) has confirmed this.

RcppParallel has the same UBSAN issues (https://www.stats.ox.ac.uk/pub/bdr/memtests/clang-UBSAN/RcppParallel/tests/doRUnit.Rout), as do other packages that use RcppParallel (e.g. gaston: https://cran.r-project.org/web/checks/check_results_gaston.html).

### ERRORs or WARNINGs

None, although see above re: UBSAN.

### NOTES

None (on macOS Sierra 10.13.4).

Only this from the results of testing on win-builder.r-project.org:

* checking installed package size ... NOTE
  installed size is  5.9Mb
  sub-directories of 1Mb or more:
    data   1.2Mb
    libs   3.0Mb

## Downstream dependencies

No errors, warnings, or notes were caused in other packages, using `devtools::revdep_check()` to confirm.
