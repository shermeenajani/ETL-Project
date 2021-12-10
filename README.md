# ETL-Project
Extract. Transform, Load Project

This project was designed to do three things (Extract, Transform, and Load):
 
EXTRACT:
We extracted the data by web scraping from two websites (Zillow and Redfin) using the python library Beautiful Soup and loading them into a Mongo Database.
For Zillow, we first have to use session request headers to avoid Zillow detecting automated requests and popping up  a captcha. Then we create a session and input an area to search. We used “Johns Creek” and grabbed the first page of listings. Luckily, on Zillow there is a large json to scrape from. We are most interested in the “Zestimate” to use for later analysis.
 
On Redfin , however, the data we want is on the detail page, so we have to call and loop through all of the detail pages. The listings are all lists of dictionaries.  Then we “find_all” of the script elements that we want to include as  json.
 
TRANSFORM:
When we only scrape the data we want and directly add it to our Mongo database, there is very little need to transform the data. However, we did have to transform some of our data from text to numbers before we added it to MongoDB.
 
LOAD:
Real estate listing websites such as Zillow often include an estimate of a home’s value (in Zillow’s case it's called a Zestimate). They do this to provide a starting point for
what a consumer should expect  before they ask for an appraisal. The real
estate brokerage website, Redfin, also provides easy to find estimates of home
values. However, realtor.com didn’t / doesn’t. What we wanted to do is to create a web scraping tool that collects data from real estate brokerage sites and loads it into our Mongo Database. Then it would be possible to use that data to perform a large number of analyses, including creating our own Proprietary estimate of home values. In python, we first set up a connection to our local Mongo Database. Then we define our database and our collection data. As we scrape our json data,  we add it to our collection primarily by using the insert_one function. After that, we can utilize the data based on how we want to analyze it.

