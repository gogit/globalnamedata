## What is this?

Most data on names and gender is ill-suited for any serious analytical purpose. Websites which collect data on birth names mainly offer searches, top ten lists and suggestions for parents. Most available data on the web comes either from commercial sources or from summary data.

We have collected birth record data from the United States and the United Kingdom across a number of years for all births in the two countries and are releasing the collected and cleaned up data here. We have also generated a simple gender classified based on incidence of gender by name. You can use this data for any purpose compatible with the [license](https://github.com/OpenGenderTracking/globalnamedata/blob/master/LICENSE.md).

And, unlike any other open record for name data, we've provided the scripts necessary to check our work! You don't need to trust us in order to trust the data.

## Setup

The easiest way to set up Global Name Data is to clone the repo and open an R console in the base directory of the project. Once there you can run `master.R` and that will bring all the necessary functions into your workspace. 

Specifically you should run

    source("master.R", chdir = TRUE)
    
in the console. That will allow R to set the correct working directory.

## Not an R user?

If you're mainly interest in the data, pre and post classified name data is available in the [data directory](https://github.com/OpenGenderTracking/globalnamedata/tree/master/data).

## Contributing

We love pull requests. While not required, please try to adhere to [Google's R Style guide](http://google-styleguide.googlecode.com/svn/trunk/google-r-style.html). 

# Data

## Data sources

Currently Global Name Data utlizes four sources:

* The United States 
    * [Social Security Administration](http://www.ssa.gov/)
* United Kingdom
    * UK [Office of National Statistics](http://www.statistics.gov.uk/hub/index.html)
    * [Northern Ireland Statistics and Research Administration](http://www.nisra.gov.uk/)
    * [Scotland General Register Office](http://www.gro-scotland.gov.uk/)

Processed data are provided under the Open Government License or the public domain where appropriate. See the [LICENSE](https://github.com/OpenGenderTracking/globalnamedata/blob/master/LICENSE.md) for details.

### United States

The Social Security Administration provides records for name and gender by year for births between 1880 and 2011. In each year, names with a minimum incidence of 5 births are counted. Prior to 1937, data should be considered suspect and retrospective as names were only recorded for individuals who received a social security card and birth year was not comprehensibly verified. More information can be found [here](http://www.ssa.gov/oact/babynames/limits.html).

### United Kingdom

Records for the United Kingdom are broken out across England and Wales, Northern Ireland and Scotland. The Office of National Statistics records births for England and Wales while Northern Ireland and Scotland are recorded seperately. In all jurisdictions the minimum number of births per year for each name is 3. Each jurisdiction provides summary data (e.g. top 10 names per year) but we do not download this data or use it in any way.

#### England and Wales

Full name data is provided between 1996 and 2011. The ONS offers historical summary data for 1904-1994 but these are restricted to the most popular names per year and so not of much analytical value. Information on the data itself can be found [here](http://www.ons.gov.uk/ons/guide-method/user-guidance/health-and-life-events/births-metadata.pdf) **[PDF]**.

#### Northern Ireland

Northern Ireland provides full name data between 1997 and 2011. Like the ONS, summary data is offered but does not add much value. Information on NISRA data can be found [here](http://www.nisra.gov.uk/demography/default.asp28.htm).

#### Scotland

Scotland only provides full name data for 2009 and 2010. Summary data is offered over the past 20 years. General information about birth record data in Scotland is available [here](http://www.gro-scotland.gov.uk/statistics/theme/vital-events/births/bckgr-info.html).

### Classification

Currently the Global Name Data project is used to produce gender estimates for byline and content classification in [Open Gender Tracker](https://github.com/OpenGenderTracking/GenderTracker). Each name is associated with a likely gender based on incidence in our name data. Future improvements will include estimates of confidence and mechanisms to test and cross-validate gender classifications.

## Dependencies

The project was built using R 2.15.2 in OS X. Any version of [R](http://www.r-project.org/) which is supported by the packages used should work but we recommend a relatively recent version. An attempt has been made to preserve portability but Windows users may experience problems as many interactions with the file system take place (especially for downloading data).

Because different governments store and expose their birth information in many different ways, Global Name Data depends on a variety of R packages for data import and handling.

__Import__

* `XML` [details](http://cran.r-project.org/web/packages/XML/index.html)
* `RCurl` [details](http://cran.r-project.org/web/packages/RCurl/index.html)
* `gdata` [details](http://cran.r-project.org/web/packages/gdata/index.html)

__Data handling__

* `plyr` [details](http://cran.r-project.org/web/packages/plyr/index.html)
* `reshape2` [details](http://cran.r-project.org/web/packages/reshape2/index.html)

`RCurl` and `gdata` will introduce external dependencies, namely Curl and perl (nearly any version in reasonable use will work). On *NIX systems this shouldn't present a problem as both should already be installed. 

Packages may be installed by typing `install.packages(c("XML", "RCurl", "gdata", "plyr", "reshape2"))` into the R console. The package installer will determine and install package dependencies as needed. Information on installing R packages is [here](http://cran.r-project.org/doc/manuals/R-admin.html#Installing-packages). Each package need only be installed once in an R environment and will persist across sessions.

# License 

See the [LICENSE](https://github.com/OpenGenderTracking/globalnamedata/blob/master/LICENSE.md) file for details.
