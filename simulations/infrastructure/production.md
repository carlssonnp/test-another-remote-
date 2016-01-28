We touched a bit on avant-basic when exploring how data moves around.  But now we're going to go a bit deeper and actually look at live production data.


## Installing avant-basic

To do this, we need to set up a copy of `avant-basic` on your local machine.

1.) [Install bundler](http://bundler.io/).

2.) [Install rvm](http://rvm.io/).

3.) [Download and run Postgres.app](http://postgresapp.com/).

4.) Open the Postgres console (type `psql`) and then:

```
CREATE ROLE <your username> WITH LOGIN;
ALTER USER <your username> WITH SUPERUSER;
CREATE DATABASE avant_dev;
CREATE DATABASE avant_basic_test;
GRANT ALL PRIVILEGES ON DATABASE avant_dev TO <your username>;
GRANT ALL PRIVILEGES ON DATABASE avant_basic_test TO <your username>;
```

This will set up all the databases you need to work locally.

5.) Within `avant-basic`, run `bundle install`.  Hopefully it will work the first time, but you may encounter errors.  Try to spend fifteen minutes reading the stacktrace of each error and using Google to solve your own problem before asking for help, but don't get stuck on each issue for too long.

6.) Once you have successfully bundled, run `bundle exec rake db:migrate`.  This will create your development database.

7.) Next run `bundle exec rake db:test:prepare`.  This will create your test database.

8.) Then run `bundle exec rake db:seed`.  This will prepopulate your database with some initial objects needed to work.

9.) Start a web server with `bin/start_development`.  Navigate to http://localhost:4000 and you can see a copy of the Avant website on your own computer!

## Prod Console

10.) Kill your server.  Now let's open the prod console!

11.) Run `avant console us`.

12.) After awhile, you will be in a production console.  You can then interact with our database using Rails's ActiveRecord instead of SQL.

13.) Skim [some docs on ActiveRecord](https://github.com/rails/rails/blob/master/activerecord/README.rdoc).  [Read a bit more about interacting with ActiveRecord](http://www.giantflyingsaucer.com/blog/?p=1891).

#### Exercises

Answer using ActiveRecord, not SQL:

* Get the object for Loan #123456.  What is its loan status?  When was it created?

* What is the name of the person holding Loan #123456?

* How many loans do we have that are "current"?


## Scoring Customers

Now it's time to do a common task for verifying models -- score models in production.

When you deploy your model, after a bit more work done by data engineers, it will also have a representation in the production console.  (Your example model won't be in the production console yet because no one hs done this extra work yet.)

For example, we can use the model "default/transunion/2.1".

In Ruby, we can inspect the model like this:

```Ruby
model = ModelSwitch.version("default/transunion/2.1")
```

We then can use it to score loans:

```Ruby
model.score(Loan.find(615750))
```

Sometimes we might want to score a loan without using the Ruby cache, to get the *true* data. (Ideally the cache will match the true data, but this is a good verification check):

```Ruby
Modeling.without_cache { model.score(Loan.find(615750)) }
```

You can compare this to the production model score from R:

```R
model <- production_model("default/transunion/2.1")
data <- batch_data(615750, "default/transunion/2.1")
model$predict(data, list(on_train = TRUE))
```

Hopefully all three of these numbers (Ruby with cache, Ruby without cache, R) should match!

This kind of test is done automatically with the alpha-beta check, but a manual spot check might be required for additional verification when trying to put a model into active production.  And now you can do it from the production console yourself!
