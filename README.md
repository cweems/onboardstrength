# On-board Strength API

This dataset is the partial list of OBS numbers from 2009 to 2012. The data reflects the numbers of Volunteers placed in regions, posts, assigned sectors, dates of service, gender, ethnicity, education level attained, and home state. 

The data is not disaggregated for privacy reasons (i.e. you cannot isolate individuals who are 'male' *and* 'education' sector volunteers in a particular country).

###About On-Board Strength Data
The On-board Strength (OBS) count is the official number of currently serving trainees and Volunteers. It is a count of all trainees and Volunteers serving on September 30 of the fiscal year, including Peace Corps Response and United Nations Volunteers, from all funding sources. This includes Volunteers funded by the President's Emergency Plan for AIDS Relief (PEPFAR). The on-board count includes posts in which the Peace Corps is active or suspended, but not closed.

####Data Definitions
`REGION` Region the individual is assigned (Africa, EMA, or IAP)  
`POST` Post the individual is assigned  

*Sector - Broad work area of the project the individual works*  
`Agriculture`  
 `Business Development`  
`Education`  
`Environment`  
`Health & HIV/AIDS`  
`Youth in Development`  
`Other`  

*Ages - Age of individual at the end of the fiscal year*
`20s`  
`30s`  
`40s`  
`50s`  
`60s`  
`70s`  
`80s`  

*Gender - Gender of individual*  
`Male`  
`Female`  

*Ethnicity - Self-reported ethnic or racial background of individual*
`African American`  
`Asian American` 
`Caucasian`  
`Hispanic`  
`Mixed Ethnicity`  
`Native American`   

###API Approach
As a proof-of-concept for the value of APIs - it is far easier to use existing public spreadsheet data (XLS or CSV) in its existing form than to build machine translators. The approach here has been to use [Project Open Data](http://project-open-data.github.io/)'s '[csv-to-api](https://github.com/project-open-data/csv-to-api)' to generate a RESTful API from the static OBS CSV data.

Note that while OBS data is available at [Peace Corps Open Data](http://www.peacecorps.gov/open/data/), it was necessary to combine the datasets in order to use the csv-to-api filtering method. That [bulk CSV](https://github.com/PeaceCorps/onboardstrength/blob/master/data/OBS_FY_9-12.csv) is can be found on the [onboardstrength Github Repository](github.com/peacecorps/onboardstrength).

###Using the onboardstrength API

####Arguments

* `source`: the URL to the source CSV
* `source_format`: if the url does not end in `.csv`, you should specify 'csv' here (to facilitate future functionality)
* `format`: the requested return format, either `json`, `xml`, or `html` (default `json`)
* `callback`: if JSON, an optional JSONP callback
* `sort`: field to sort by (optional)
* `sort_dir`: direction to sort, either `asc` or `desc` (default `asc`)
* any field(s): may pass any fields as a key/value pair to filter by that field

####Example Usage

**Get CSV as JSON** (default behavior)  
[CSV to JSON](http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv)  
http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv

**Get results as XML**  
[CSV to XML](http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml)  
http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml

**Get results as JSONP**  
[CSV to JSONP](http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=html)  
http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=json&callback=parse_results

### Get results as HTML
[CSV to HTML](http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=html)  
http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=html


### Sort by a field
* [Sort by Post (HTML) (ascending)](http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=html&sort=Post&sort_dir=asc)  
http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=html&sort=Post&sort_dir=asc

* [Sort by Total Volunteers (HTML) (descending)](http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=html&sort=Total%20Volunteers%20at%20Post&sort_dir=desc)  
http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=html&sort=Total%20Volunteers%20at%20Post&sort_dir=desc

### Filter by a field
* [Filter by Region - Africa (HTML)](http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=html&Region=AF)  
http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=html&Region=AF

* [Filter by Year - 2011 (HTML)](http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=html&Year=2011)  
http://labs.data.gov/csv-to-api/?source=https://github.com/PeaceCorps/onboardstrength/raw/master/data/OBS_FY_9-12.csv&format=xml&format=html&Year=2011

###Usage
License is GPLv3 or later.