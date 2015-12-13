We're a pretty secure company, so you'll need access to various things.  This will prevent you from doing real work for a bit, so focus on going through this onboarding guide while making sure that you're on top of getting access to these.

To get started with working on analytics at avant, begin with the following setup. We assume you have a Mac and are using OS X.

1. Set up HipChat.  You should have received a link to configure hipChat in e-mail.  If not, contact Guadian & IT.  Join the rooms: `Analytics` and `Analytics General`.  Also join `LA data science`.
 
2. Install [iTerm2](https://iterm2.com/downloads.html) and move it to your Applications folder.

3. Open iTerm2 and type
   
   ```bash
   ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   brew install libcurl-dev
   brew install postgres
   brew update
   brew install caskroom/cask/brew-cask
   brew cask install r
   ```

   If `brew install libcurl-dev` fails, try `brew install curl`

4. Install the [Xcode command line tools](http://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/). 

5. Install [Java 6](https://support.apple.com/kb/dl1572?locale=en_US).

6. Set up your [git ssh key](https://help.github.com/articles/generating-ssh-keys/).

7. Have Rob K add your github account to the credit-model group of the avantcredit organization.

8. Set up your [Github oauth token](https://gist.github.com/robertzk/c6efef69a92cc3a03753) and put it in your `~/.bash_profile`:
      
   ```
   export GITHUB_PAT=token_goes_here
   ```

   Note there are no spaces around the `=`.
      
9. Reload your .bash_profile:

   ```bash
   source ~/.bash_profile
   ```

10. Open up R and run the following to install our dependencies:

   ```r
   install.packages("devtools")
   devtools::install_github("robertzk/allthepackages")
   allthepackages::install_all()
   dir.create("~/dev", FALSE, TRUE); dir.create("~/tmp", FALSE, TRUE)
   setwd("~/dev")
   system("git clone git@github.com:avantcredit/avant.git")
   system("git clone git@github.com:avantcredit/avant-analytics.git")
   q()
   ```

11. Get an `~/.Rprofile` from someone else.

12. Get Amazon S3 credentials and a `database.yml` file from Rob K.  Install your `database.yml` file in `~/dev/avant-analytics/config/database.yml`.  This will let you connect to all our databases and caching layers.

13. In terminal, navigate to `~/dev/avant-analytics` and start R. If you eventually see the following, then you have successfully installed all the packages you need to start your journey across the Syberian Tundra.

   ```r
   ...
   Installing gbm 2.1.6 from github
   |++++++++++++++++++++++++++++++++++++++++++++++++++| 100%
   ```
      
14. If you have trouble installing `gbm`, it's probably complaining about gfortran.  Try the instructions [here](http://thecoatlessprofessor.com/programming/rcpp-rcpparmadillo-and-os-x-mavericks-lgfortran-and-lquadmath-error/), *in your terminal*, i.e.:
      
   ```
   curl -O http://r.research.att.com/libs/gfortran-4.8.2-darwin13.tar.bz2
   sudo tar fvxz gfortran-4.8.2-darwin13.tar.bz2 -C /
   ```

15. Setup you .s3cfg file. This setups up your credentials to read and write to AWS S3, our cloud storage space. 

   ```bash
   brew install s3cmd
   ```

   Ask Rob K. or Tong Lu for credentials and then copy and paste [this](https://gist.github.com/peterhurford/023bcaee0a27fa77e814) into your `~/.s3cfg` file.
   Replace `{INSRET YOURS HERE}` with your credentials. Test out your connection with the following:

   ```bash
   s3cmd ls s3://avantminer/tmp/
   ```

16. Be able to [log into an EC2 instance](https://github.com/avantcredit/avant-analytics/wiki/Configure-your-new-EC2-instance)

17. Set up Pivotal Tracker
