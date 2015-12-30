## The "Big Model" Problem

A lot of companies talk about "big data". This term is overused. Every time we go to conferences, people ask us how big our data sets are. Real data scientists don't really care.

At Avant, we do not have a big data problem. Most of our data sets are around 350K rows and 300 columns. Occasionally, when working with unaggregated tradeline data, direct mail data, or cashflow models, maybe we'll have 10-100M rows. There has only been one data set in the history of the team that has not fit on disk. So very little that we do involves big data.

Instead, we think the much more critical problem is "big model". How do we build dozens of predictive models, simaltaneously, quickly, efficiently, accurately, production-ready, at scale? If we want to support three kinds of models (marketing + operations + default) across four kinds of products (unsecured loans + auto loans + credit cards + mortgages) within four different regions (US + UK + Canada + Australia), that's 48+ models we need to make.

Solving this "big model" challenge is the goal of our team.


## Data Science

The Data Science team is split into two parts: Data Science and Data Engineering.  This key split is a matter of focus: we all need to know statistics and programming, but which one are you more focused on?  Data scientists tend to be good at programming but great at statistics, whereas data engineers are great at programming but only merely good at statistics.  This is different from a generic Ruby developer who is great at programming but knows nothing about statistics...  We're all data scientists, but some of us focus on engineering.

![](http://101.datascience.community/wp-content/uploads/2014/07/data-scientist-vs-data-engineer.jpg?w=500)


## Data Science Teams

* Tong Lu, Lead Data Scientist, oversees all the Data Science teams.

* **Data Science R&D** - Fei Ye, lead (CHI) + Eddie Herman (CHI) + Matt Meng (LA).  This team focuses on cutting-edge statistics work to improve model performance, such as trying out new classifiers.

* **Data Science, Core Business** - Yuchen Yang, lead (CHI) and David Nguyen, lead (LA). This team does the core work needed to get models out.  These models include the 48+ models discussed previously, across all the products, geographies, and business areas.


## Data Engineering Teams

* Robert Kryzyzanowski, Lead Data Engineer, oversees all the Data Engineering teams.

* **Infrastructure** - David Feldman, lead (CHI) + Jing Zhu (CHI). This team builds the Ruby infrastructure needed to interface with the front-lines, getting data from customers and ensuring customers are getting scored.

* **Deployment** - Kirill Sevastyanenko, lead (CHI). This team (currently a team of one) focuses on the R infrastructure and DevOps needed to productionize Syberia models and give scores to the Ruby side.

* **APIs and Tooling** - Peter Hurford, lead (CHI) + Khalid Harun (CHI) + Elaine Lee (CHI) + Abel Castillo (CHI) + Daniel Braithwaite (CHI). This team does everything else that isn't coveed by Infrasturuce or Deployment. This usually means a focus on R programming around APIs that bring data into building models as well as some work on the Syberia framework for building models in development.  This team also handles a lot of the QA and data integrity monitoring to make sure things don't break.

* **LA Team** - Ryan Naughton, lead (LA) + Dave Boren (LA). This team works in LA and helps out the other DE teams as needed.
