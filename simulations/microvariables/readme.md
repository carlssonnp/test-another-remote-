## Microvariables

Now that you know where data comes from, let's look at a particular source you will likely use often - microvariables!

While some of our data requires Ruby-specific magic to work, a lot of our variables are just simple (or complex!) SQL queries on the database.  These SQL queries are called **microvariables** and live on a standalone microvariable server microservice.

One does not need to create the corresponding ruby code as this will be automatically done under the hood, thus increasing iteration speed. This allows data scientists to contribute variable ideas using SQL without (a) nedding to know how to work in avant-basic or (b) deal with the slow, 1+ day PR + deploy process to change a variable. The microvariable server can be updated in mere minutes!

#### Reading

* Read [the microvariable server documentation](https://github.com/avantcredit/analytics-microvariable-server/blob/master/README.md).

#### Exercises

1. Use the [web UI](microvariable-dev.avant.com) to create a custom microvariable of your choice.

2. Use `batch_source` to read data from your microvariable for a random loan. What are the dimensions?

3. Add your microvariable to your model's import stage.

4. Re-run your model (remember to set `options(avant.limit = 500)` first).  Does your microvariable work?

5. Does your microvariable add lift?  Compare your model with and without that variable using a lift chart to find out.

6. What is the difference between a UK microvariable and a US microvariable?
