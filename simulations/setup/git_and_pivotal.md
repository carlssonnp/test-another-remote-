## Git 102

Add yourself to the [team list](https://github.com/avantcredit/avant/blob/master/R/team.R). To do this, you'll not only have to use your git skills, but you'll have to know some other things:

* You must "version" your contribution by updating the files `DESCRIPTION` and `CHANGELOG.md`, which means indicate your change with a version number (e.g., 0.3.15.9002) so that we can track changes.  Use this [PR](https://github.com/avantcredit/avant/pull/865/files) as a template. [Read about versioning here.](http://semver.org/)

* You must be compliant with our [the PR Checklist](https://github.com/avantcredit/avant-analytics/wiki/PR-Review-Checklist).

* You must be [compliant with SOC2](https://github.com/avantcredit/avant-analytics/wiki/Compliance-(SOC-2)) (see "Pivotal" below).


## Status Checks

* Whenever you make a PR, tests for the repository will automatically be run and will need to be passed before you can merge a PR. This should not be a problem for your PR and you'll learn more about tests later.

* You'll also need two different people to approve your PR with an "LGTM". (You can be one of those two people.) 


## Pivotal

* Read about [how Pivotal Tracker works](https://www.pivotaltracker.com/help/articles/quick_start/).

* Read about [how we use Pivotal Tracker](https://github.com/avantcredit/avant-analytics/wiki/How-Avant-Analytics-Uses-Pivotal).

* Create a SOC2 compliant Pivotal task [using this template](https://www.pivotaltracker.com/story/show/120859655) and link it into your PR. ([Here's an example of a completed one](https://www.pivotaltracker.com/n/projects/1257760/stories/118044149).)


## SOC2 Exercises

1.) I want to update the lockfile to include the latest avant package version.  Do I need to follow SOC II?  Do I need to use the DE checklist?  Do I need to use the DS checklist?

2.) I'm adding a new model to `models/dev`. Do I need to follow SOC II?  Do I need to use the DE checklist?  Do I need to use the DS checklist?

3.) I'm adding a new model to `models/dev`, but in doing so, I change the way data sources are processed for all models. Do I need to follow SOC II?  Do I need to use the DE checklist?  Do I need to use the DS checklist?

4.) I'm adding a new data source to `avant-basic`. This data source will never be used in production. Do I need to follow SOC II?  Do I need to use the DE checklist?  Do I need to use the DS checklist?

5.) My PR has a Pivotal link with the proper SOC II documentation.  I got Kirill to say my code looks good to merge.  What one last step needs to be done to finish compliance with SOC II?
