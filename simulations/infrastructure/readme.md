## Reading

So far you've been using Syberia to build and deploy your model.  Now it's time to dive a bit deeper and understand the infrastructure:

* Read the [Syberia website](http://syberia.io/) for explanation of what the Syberia framework is.
* Read the [open source documentation for Syberia](https://github.com/syberia/syberia/blob/release_candidate1/README.md).

* [Read about the structure of Syberia](https://github.com/avantcredit/avant-analytics/blob/master/README.md).

* [Read more about director](https://github.com/syberia/director/blob/documentation_cleanup/README.md), the R package for managing a directory of R scripts.  Director resources are like a superpowered version of `source` and form the backbone of Syberia.

* Read a bit about [how to use stagerunner independently from Syberia](https://github.com/avantcredit/avant-analytics/wiki/How-to-use-StageRunner-(outside-of-Syberia)).


## Exercises

* Run the [example Syberia file](https://github.com/syberia/example.sy). Did it work?
* What is a "stagerunner"?
* What is a "tundraContainer"?
* What is the point of the `config` folder?
* What is a "resource"?  How is it different from `base::source`?
* What is a "controller"?  How are controllers used when running a Syberia model?
* How would one run a subset of the mungeprocedure on arbitrary data given a TundraContainer? 
