We touched a bit on avant-basic when exploring how data moves around.  But now we're going to go a bit deeper and actually look at live production data.


## Installing avant-basic

1.) Clone [github.com/avantcredit/avant-basic](https://github.com/avantcredit/avant-basic) to your favorite directory.

2.) Add the following to `config/database.yml` and update `username`:

```
general: &general
  adapter: postgresql
  min_messages: ERROR

development: &development
  host: localhost
  adapter: postgresql
  encoding: unicode
  database: avant_dev
  username: <your username REPLACE ME!!!>

production: &production
  <<: *development

test: &test
  <<: *development
  database: avant_basic_test
```

3.) [Install bundler](http://bundler.io/) if you don't have it. Make sure you have version 1.11.2.

4.) [Install rvm](http://rvm.io/).

5.) Install the [Heroku toolbelt](https://toolbelt.heroku.com/): `brew install heroku-toolbelt`

6a.) Install [Redis](http://redis.io/): `brew install redis`.

6b.) Then add Redis to your startup list with `ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents`.

6c.) Then start Redis with `launchctl load ~/Library/LaunchAgents/homebrew.mxcl.redis.plist`.

7a.) Download and run [Postgres.app](http://postgresapp.com/). To match up with avant-basic you need to use the old **9.4.5** version, which [you can download from their GitHub page](https://github.com/PostgresApp/PostgresApp/releases/tag/9.4.5.0) (download Postgres-9.4.5.0.zip, open it, and run the installer).

7b.) Make sure the `psql` command works. If not, you might have to modify your `$PATH` to include the correct location of your postgres app. You can check your current path for psql with `which psql`.

7c.) Ensure that `psql --version` is 9.4.x. If not, you need to change the version. If you change the version you have installed, be sure to also `gem uninstall pg` and `bundle install` because your pg gem will have been compiled against your old (wrong) version.

7d.) Open the Postgres console (type `psql`) and then:

```
CREATE ROLE <your username> WITH LOGIN;
ALTER USER <your username> WITH SUPERUSER;
CREATE DATABASE avant_dev;
CREATE DATABASE avant_basic_test;
GRANT ALL PRIVILEGES ON DATABASE avant_dev TO <your username>;
GRANT ALL PRIVILEGES ON DATABASE avant_basic_test TO <your username>;
```

This will set up all the databases you need to work locally.

8a.) Within `avant-basic`, run `bundle install`.  Hopefully it will work the first time, but you may encounter errors.  Try to spend fifteen minutes reading the stacktrace of each error and using Google to solve your own problem before asking for help, but don't get stuck on each issue for too long.

8b.) Once you have successfully bundled, run `bundle exec rake db:migrate`.  This will create your development database.

8c.) Next run `bundle exec rake db:test:prepare`.  This will create your test database.

8d.) Then run `bundle exec rake db:seed`.  This will prepopulate your database with some initial objects needed to work.

9a.) Start a web server with `bin/start_development`.  Navigate to http://localhost:4000 and you can see a copy of the Avant website on your own computer!

9b.) *optional* - Use the web server to apply for a fake loan, if you're curious.

## Prod Console

10a.) Kill your server (ctrl+C in your terminal).  Now let's open the prod console!

10b.) Run `avant console us`.

10c.) After awhile, you will be in a production console.  You can then interact with our database using Rails's ActiveRecord instead of SQL.

11.) Skim [some docs on ActiveRecord](https://github.com/rails/rails/blob/master/activerecord/README.rdoc).  [Read a bit more about interacting with ActiveRecord](http://www.giantflyingsaucer.com/blog/?p=1891).

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
