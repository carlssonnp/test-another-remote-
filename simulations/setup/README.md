We're a pretty secure company, so you'll need access to various things.  This will prevent you from doing real work for a bit, so focus on going through this onboarding guide while making sure that you're on top of getting access to these.

To get started with working on analytics at avant, begin with the following setup. We assume you have a Mac and are using OS X.

# General setup

1: Set up HipChat.  You should have received a link to configure hipChat in e-mail.  If not, contact Guadian and IT.  Join the rooms: `Analytics` and `Analytics General`.  Also join `LA data science`.  (You make requests to IT through the [ServiceNow portal](https://avantcreditcorp.service-now.com/navpage.do).)
 
2: Install [iTerm2](https://iterm2.com/downloads.html) and move it to your Applications folder.

3: Install the [Xcode command line tools](http://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/). 

4: Install [Java 6](https://support.apple.com/kb/dl1572?locale=en_US).

5: Set up Pivotal Tracker.  Ask Tong Lu for access.

6a: Make an account on [Heroku](www.heroku.com) with your Avant email address.

6b: [Ask IT](https://avantcreditcorp.service-now.com/navpage.do) for access to "avant-prod" on Heroku. This is the server we host avant.com on for the US.

6c: Ask IT for access to the corporate calendar and the Analytics OOO calendar.

6c: Ask IT (in a separate ticket) for access to CircleCI.


# Github access

7a: Set up your [git ssh key](https://help.github.com/articles/generating-ssh-keys/).

7b: Add your public key to https://github.com/avantcredit/public_keys

8a: Set up [two factor authentication](https://github.com/blog/1614-two-factor-authentication).

8b: Submit a ServiceNow ticket to IT to add your github account to the credit-model group of the avantcredit organization.

9: Set up your [Github oauth token](https://gist.github.com/robertzk/c6efef69a92cc3a03753) and put it in your `~/.bash_profile`:
      
   ```
   export GITHUB_PAT=token_goes_here
   ```

   Note there are no spaces around the `=`.
      
10: Reload your .bash_profile:

   ```bash
   source ~/.bash_profile
   ```

# R installation and setup

11: Open iTerm2 and type
   
   ```bash
   ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   brew install libcurl-dev
   brew install postgres
   brew update
   brew install caskroom/cask/brew-cask
   brew cask install r
   ```

   If `brew install libcurl-dev` fails, try `brew install curl`

12: Get an `~/.Rprofile` from someone else. You should have two `Rprofile`s, one at `~/.Rprofile` and the other at `~/dev/avant-analytics/.Rprofile` (which comes with the avant-analytics repo so you probably already have it). They're different and you want both of them!

13a: See if you can login at avant.looker.com. If that doesn't work, request access by following [the BI onboarding guide here](https://wiki.ad.avant.com/display/BI/BI+100%3A+Accounts+and+Software).

13b: Ensure that you have:

```
export LOOKER_URL="https://avant.looker.com:19999/"
export LOOKER_ID="yourid"
export LOOKER_SECRET="yoursecret"
```

...somewhere in your `~/.bash_profile` (or equivalent). To get your looker credentials, please reach out to Ignacio Thayer or your Gaurdian.

14: Ensure that your analytics ETL is set up. [Follow the instructions here.](https://github.com/avantcredit/analyticsetl/blob/master/README.md)

15a: In terminal, navigate to `~/dev/avant-analytics` and start R. If you eventually see the following image, then you have successfully installed all the packages you need to start your journey across the Syberian Tundra.

<img src="https://camo.githubusercontent.com/7f158ab3c80778a5f4c7c52886a46275038e3907/687474703a2f2f7075752e73682f707a4155752f363866613935666233392e706e67" alt="alt text" width="300" height="300">

15b: If you have trouble installing `gbm`, it's probably complaining about gfortran.  Try the instructions [here](http://thecoatlessprofessor.com/programming/rcpp-rcpparmadillo-and-os-x-mavericks-lgfortran-and-lquadmath-error/), *in your terminal*, i.e.:
      
   ```
   curl -O http://r.research.att.com/libs/gfortran-4.8.2-darwin13.tar.bz2
   sudo tar fvxz gfortran-4.8.2-darwin13.tar.bz2 -C /
   ```
15c: If you do not see the above image and you get an xgboost error, try the steps in this [http://xgboost.readthedocs.io/en/latest/build.html#r-package-installation](http://xgboost.readthedocs.io/en/latest/build.html#r-package-installation). If these steps don't work, as for help.

# S3, EC2, and Microvariables

16: Get Amazon S3 credentials and a `database.yml` file from Rob K.  Install your `database.yml` file in `~/dev/avant-analytics/config/database.yml`.  This will let you connect to all our databases and caching layers.

17: Setup your .s3cfg file. This sets up your credentials to read from and write to AWS S3, our cloud storage space. 

   ```bash
   brew install s3cmd
   ```

   Ask Rob K for credentials and then copy and paste [this](https://gist.github.com/peterhurford/023bcaee0a27fa77e814) into your `~/.s3cfg` file.
   Replace `{INSERT YOURS HERE}` with your credentials. Test out your connection with the following:

   ```bash
   s3cmd ls s3://avantminer/tmp/
   ```

18a: Ask RobK for an EC2 instance account.

18b: Be able to [log into that EC2 instance account and configure it](https://github.com/avantcredit/avant-analytics/wiki/Configure-your-new-EC2-instance).
