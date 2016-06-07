## Disclaimer

**No cheating!** You're only cheating yourself and making yourself a worse employee by not doing this for yourself!

## Git

#### Exercise 4

https://github.com/avantcredit/analytics-onboarding/blob/master/simulations/setup/git.md

**How do you see the files changed within each commit from git log?**

**How do you see the contents of what changed within each file from the git log?**

**What does HEAD refer to in the context of git? (Not to be confused with the "HEAD<<<<" one observes within merge conflict)**


## Advanced R

See [my Advanced R solutions](https://github.com/peterhurford/adv-r-book-solutions).

TODO: Exercises in http://r4ds.had.co.nz/transform.html, http://r4ds.had.co.nz/functions.html, http://r4ds.had.co.nz/visualize.html, http://r4ds.had.co.nz/tidy.html


## R Pacakges

**What are the three requirements when naming an R package?**

1.) Only letters, numbers, and periods are allowed. (But periods are discouraged.)
2.) It must start with a letter.
3.) It cannot end with a period.

**Why is it a bad idea to name your package with a "."?**

It creates confusion with R's built-in S3 methods.

**What is the difference between devtools::install_github and install.packages?**

`install.packages` installs from CRAN and is built into base R.  `devtools::install_github` installs from a GitHub repository and is a from a separate package written by Hadley.

**What is the difference between devtools::build and devtools::install?**

`devtools::build` will take a pacakge and create the `tar.gz` file that can be installed.  `devtools::install` will build and then actually install the package.

**What is the difference between devtools::load_all and library?**

`library` takes an installed package and loads it into memory.   `devtools::load_all` also loads the package into memory, but can load the package into memory even if it isn't installed.  (`devtools::load_all` does not actually install the package, thoguh.)

**What is the difference between Suggests and Imports?**

Packages listed in `Imports` are mandatory and will be automatically installed when the package is installed and the package will not install if any of these dependencies error on their installation.  `Suggests` are optional, will not be installed by default, and the package can be installed without them.

**What is the importance of dontrun?**

Your examples in your documentation are run by default in R and their output is appended to the documentation.  Furthermore, if an example fails to compute, this error will be reflected when `R CMD CHECK` is run.  `dontrun` prevents an example from being run.

**Why do packages have versions?**

So you can track changes between packages and rollback to previous changes if needed.

**What does moving from v1.0.1 to v2.0.0 mean? What does moving from v1.0.1 to v1.0.2 mean?**

Moving from v1.0.1 to v2.0.0 is a major change, which usually means a lack of backwards compatability.  v1.0.1 to v1.0.2 is indicative of a patch, which is a very small change that does not affect core functionality.

**What does v1.0.1.9000 mean?**

That the package is in development and is likely not stable.


## ISL

* See [my chapter 2 answers](https://github.com/peterhurford/statsnotes/blob/master/intro_stats_learning/02_statistical_learning/exercises.md).


## GBM

* TODO: https://github.com/avantcredit/analytics-onboarding/blob/master/simulations/mathematical/gbm/readme.md


## Business

**Who is David Pickel?**

He's the company contorller.

**How many employees do we have?**

Over 800

**When was Avant founded?**

December 2012

**Which countries are we in?**

US, UK, and Canada.  Australia forthcoming.

**What is "debt consolidation"? Why would someone want to do that?**

Debt consolitation is when you take out a loan at a lower interest rate (e.g., an Avant loan) to pay off a pre-existing loan at a higher interest rate (e.g., credit card debt).  This is desirable for the consumer because it saves them money.

**How is an Avant loan different from a home equity loan?**

A home equity loan is a loan secured with the value of a home owned by the loanee.  Avant does not secure loans with home equity.

**How is an Avant loan different from a payday loan?**

Payday loans are short-term loans (usually a few weeks) at exceptionally high APR (usually over 100% when annualized).  Avant loans are long-term (a few years) and typically don't exceed 36% APR.

**What is "the waterfall"?**

The ordering of accounting buckets to which payments are applied.  They first pay off fees, then interest, then principal.

**Name thre variables we cannot legally use to score a customer.**

Race, religion, sex.

**Name two factors of your FICO score.**

1.) To what degree you pay bills on time.
2.) How much money you already owe.

**How long will a bankruptcy affect your credit score?**

Up to 10 years.

**Why might someone not have a FICO score?**

Someone might be an immigrant (no social security number) or might be a recent college graduate with no credit history.

**What is the difference between hard fraud and soft fraud?**

Hard fraud is fraud involving identity theft.  Soft fraud does not involve identity theft, just a deliberate nonpayment.

**When do we issue a loan as a WebBank loan and when do we issue a loan as an Avant loan?**

WebBank has more strict rules for qualifying loans and caps APR at 36%.  Avant loans are any loans we issue that are not WebBank loans.  Right now, we only issue Avant loans for our products other than our US unsecured personal loan product.

**On which step of the Five Step App do we pull Iovation data?**

After the submission of Step 2.


## SQL

TODO: https://github.com/avantcredit/analytics-onboarding/blob/master/simulations/domain_knowledge/database_tables/readme.md


## Running a Syberia File

TODO: https://github.com/avantcredit/analytics-onboarding/blob/master/simulations/running_syberia_file/README.md


## Mungebits

TODO: https://github.com/avantcredit/analytics-onboarding/blob/master/simulations/mungebits/readme.md


## Testing

TODO: https://github.com/avantcredit/analytics-onboarding/blob/master/simulations/testing/readme.md


## Model Card

TODO: https://github.com/avantcredit/analytics-onboarding/blob/master/simulations/modelcard/readme.md


## Deployment

TODO: https://github.com/avantcredit/analytics-onboarding/blob/master/simulations/deployment/readme.md


## Syberia Infrastructure

**Run the example Syberia file. Did it work?**

It worked!

**What is a "stagerunner"?**

A stagerunner is a nested tree of stages, some of which may be stagerunners.  Each stage is executed in series, updating the stagerunner object.  Stages can be rolled back and replayed.

**What is a "tundraContainer"?**

A tundra container is an object that stores a model capable of predicting on data along with all the metadata needed to render correct predictions (e.g., how to munge the data).

**What is the point of the config folder?**

It contains configuration files and global settings for the Syberia project.

**What is a "resource"? How is it different from base::source?**

A resource is a director method that accesses a particular file using the Syberia controller.  The controller is a wrapper around `source` that may include preprocessing and postprocessing.  The plain controller is simply `base::source`.

**What is a "controller"? How are controllers used when running a Syberia model?**

A controller contains rules for how to handle a particular class of files, such as models.  Running a Syberia model uses the models controller.

**How would one run a subset of the mungeprocedure on arbitrary data given a TundraContainer?**

```R
container$munge(dataframe, 1:3)  # Use first three munging steps on dataframe.
```


## Our R Package Ecosystem

**How do I use the s3cmd command line tool to find the size of an S3 object?**

```
s3cmd ls s3://avantminer/tmp/test/test # 422370445
```

**How does one display in a human readable form?**

```
s3cmd ls -H s3://avantminer/tmp/test/test # 402M
```

**How do I use pryr::object_size to see the size of that object in R? Why might these two numbers be different?**

TODO

**How do I write a test to check that the "cache" table exists in my database?**

```R
dbtest::db_test_that("My database has a test table", {
    expect_table("cache")
})
```

**How do I write a test that executes as if it was one day prior to right now?**

```R
pretend_now_is("1 day ago", {
  test()
})
```

**What does stop = TRUE do in batchman?**

If an error occurs in a batch, the entire processing will crash with the error message.

**How do I use lockbox to install a package from my local directory?**

```
name: yourpkg
version: 0.1.0
remote: local
dir: /your/pkg
```


## Data Infrastructure

**Try calling batch_source to get transunion313 data for a random customer. What is the size of the dataframe you get back?**

```R
id <- fetch_random_loan_id()  # 1062465
> batch_source(id, "transunion313") %>% dim
[1]   1 320
```

**What is the role of request_operation in getting data?**

`request_operation` makes API calls to the Ruby APIs.

**Which file does avant-basic use to process requests for data?**

app/controllers/api/credit_models_controller.rb


## Production

**Get the object for Loan #123456. What is its loan status? When was it created?**

```Ruby
Loan.find(123456).status # "paid_off"
Loan.find(123456).created_at # Fri, 13 Jun 2014 14:35:28 CDT -05:00
```

**What is the name of the person holding Loan #123456?**

```Ruby
Loan.find(123456).customer.person.name # "Greg Poulson"
```

**How many loans do we have that are "current"?**

```Ruby
Loan.current.count  # 257790
```


## Microvariables

TODO https://github.com/avantcredit/analytics-onboarding/blob/master/simulations/microvariables/readme.md


## Follow the Rules

**1.) I want to update the lockfile to include the latest avant package version. Do I need to follow SOC II? Do I need to use the DE checklist? Do I need to use the DS checklist?**

No, no, no.

**2.) I'm adding a new model to models/dev. Do I need to follow SOC II? Do I need to use the DE checklist? Do I need to use the DS checklist?**

No, no, yes.

**3.) I'm adding a new model to models/dev, but in doing so, I change the way data sources are processed for all models. Do I need to follow SOC II? Do I need to use the DE checklist? Do I need to use the DS checklist?**

No, yes, yes.

**4.) I'm adding a new data source to avant-basic. This data source will never be used in production. Do I need to follow SOC II? Do I need to use the DE checklist? Do I need to use the DS checklist?**

Yes, no, no.

**5.) My PR has a Pivotal link with the proper SOC II documentation. I got Kirill to say my code looks good to merge. What one last step needs to be done to finish compliance with SOC II?**

Get a PM to sign off.


## Refactoring

**What is "flog"?**

Flog is an opinionated scoring system for evaluating the complexity of Ruby code.  It focuses on the number of assignments and the number of conditional branches in code, and penalizes metaprogramming.

**What is the "squint test"?**

The squint test involves looking at the structure of the code, checking whether there is a lot of idnentation (bad!) and whether similar code units (based on text editor colors) are grouped together (good!)

**Why is it a bad idea to have a 43-line conditional statement?**

It's too complex and hard to maintain.

**Why are tests important for refactoring? Why do you not refactor until tests are passing?**

Tests are important to make sure that your refactor does not break any code functionality.  Refactoring while tests are not passing increases the risk of breaking code and not understanding how to get the code back to green.

**What does "open / closed" mean? Why does that matter?**

A code is **closed** if it has a well-defined specification and future uses of it don't require modification.  It is **open** if it can be extended.  Code that is both open and closed can be used / extended without changing it.  For example, adding an additional object that inherits from it works without changing the original object.


**When is violating DRY okay?**

It is okay to have intermediate duplication while you are exploring the code to discover the correct abstraction to use to clean up the code.


## History

**Take a brief moment to contemplate and be grateful. Easier said than done. Ok good. Now you can go back to cursing about bugs.**

Always :)

**Go into production console and grab TU313 data for a loan by hand, store it in RubyRMPI and read it back in R. Then use batch_source to get TU313 data for that same loan. Do the two dataframes match?**

```
cd ~/dev/avant-basic
avant console us
```

```Ruby
lid = Loan.current.last.id  # 1421747
data = Modeling::DataSources::Transunion313.new.fetch(Loan.find(lid))
data.length # 319
RubyRMPI.store(data, "tmp/onboarding/tu313")
```

```
cd ~/dev/avant-analytics
R
```

```R
ruby_data <- rubyread("tmp/onboarding/tu313")
r_data <- batch_source(1421747, "transunion313")
length(ruby_data)
[1] 319
dim(r_data)
[1] 1 320
setdiff(names(ruby_data), names(r_data))
character(0)
setdiff(names(r_data), names(ruby_data))
[1] "loan_id"
isTRUE(all.equal(ruby_data, r_data))
[1] FALSE
```

They're not equal yet, but this is just because of a harmless difference in formatting:

```R
# Give ruby_data the loan id.
ruby_data$loan_id <- 1421747
# Sort both lists so that different orders don't break equality.
r_data <- as.list(r_data) %>% names(.) %>% order(.) %>% as.list(r_data)[.]
ruby_data <- ruby_data %>% names(.) %>% order(.) %>% ruby_data[.]
# Create consistency between NA and NULL
ruby_data[names(Filter(is.null, ruby_data))] <- NA_character_
r_data[names(Filter(is.na, r_data))] <- NA_character_
# And now it's equal!
isTRUE(all.equal(ruby_data, r_data))
[1] TRUE
```

**What Language was original GLMNET package programmed in?**

TODO
