---
layout: article
title: North Seattle Crime Project Intro
modified: null
categories: posts
tags: 
  - Seattle crime
comments: true
published: true
image: 
  feature: null
  teaser: null
  thumb: null
---









# Seattle Crime!

I recently attended my first [Open Seattle](http://openseattle.org/), hosted at [Socrata](https://www.socrata.com). There were a lot of great people there and interesting projects. While my main interests lie in health data and transportation data, one of the projects introduced that night was to help people in NW Seattle understand local crime data. This sounded like a lot of fun, plus Socrata and the [Open Data Network](http://www.opendatanetwork.com/) are like "data crack" to me, so really any excuse to analyze data is good enough for me. This is also a project close to home, since I live in one of the neighborhoods of interest.  After the meeting I signed up for [Next Door](https://nextdoor.com/city/seattle--wa/) and started trying to figure out an approach. Here is my strategy, most definitely a work in progress.  Hopefully a variety of people will be involved in the project who can bring their own ideas and perspectives to enrich or redirect the strategy below.

## The Strategy

- **Define the customer and what they want:**
    + **The customer:**  The customer is a resident of the NW Seattle neighborhoods, specifically Greenlake, Greenwood, Phinney, Broadview, and Bitterlake. This includes me.
    + **What do they want?** Ultimately people want less/no crime. Practically speaking I think people would like to be empowered and not feel helpless against crimes, ranging from petty package thefts and vandalism all they way up to violent crimes. For example, if people were to understand what crimes are occuring that are community preventable vs. what crimes are occuring the require police assistance, this could be helpful. From reading Next Door threads it sounds like people would really like to increase police resources in this area. One suggested way to do this was to report all crimes or to track unreported crimes. Maybe we could develop a tool for this or present one that already exists.


- **Determine goals. Potential goals include:**  
    + Inform NW Seattle residents about available crime data resources and help them understand the data
    + Use the data to empower NW Seattle residents and enable action, such as more effective crime prevention or re-allocation of city resources.
    + Develop a persistent resource (e.g. a website or app) which will help continue and reinforce empowerment


- **Determine tactical approach to achieve goals:**
  + How can we best present the data and resources (visualization types etc.)?
  + What is the best way to present the data (pub night, local library, website, musical, morse code)?


- **Determine resources and methods:** I try never to reinvent the wheel. One hour in the library can save you a week in the lab.
  + What data resources are available?
  + What analyses have other people done on Seattle Crime data?
  + What analyses have other people done on crime data in other cities that we can apply?
  + What tools are currently available?

  ### Selected Data Resources
  Note that in general the city website, Open Data Network, and Socrata are great resources. The [SODA API](https://dev.socrata.com/consumers/getting-started.html) will be very handy if we decide to build an application.

  - [police report incident API](https://dev.socrata.com/foundry/data.seattle.gov/y7pv-r3kh)
  - [police report offense API](https://dev.socrata.com/foundry/data.seattle.gov/6thv-9ipt)
  - [police 911 response API](https://dev.socrata.com/foundry/data.seattle.gov/pu5n-trf4)
  - [crimes by precinct 2008 to present API](https://dev.socrata.com/foundry/data.seattle.gov/hapq-73pk)
  - [crime stats by 1990 census tract 1996 to 2007 API](https://dev.socrata.com/foundry/data.seattle.gov/5r5q-9au5)
  - [police department beats API](https://dev.socrata.com/foundry/data.seattle.gov/xjqu-9v63)
  - [seattle zip codes API](https://dev.socrata.com/foundry/data.seattle.gov/5iir-m2en)
  - [seattle block watch data](https://data.seattle.gov/Public-Safety/Block-Watch/n3gw-htbc)
  

  ### Selected Tools, Analyses, Visualizations, Applications, and Code
  There are a lot of analyses out there, but not all of them are relevant to our purposes.  Below are resources and examples found that are particularly relevant.
  
  - [Trulia Crime Map](http://www.trulia.com/real_estate/Seattle-Washington/crime/): This an interactive crime map that has a heat map component for crime risk. It is built primarily from spotcrime.com data. The Seattle component of spotcrime.com is built from SPD data via some of the data resources above, which is accesible through the SODA API.....yada yada, I think you see where I am going with this. 
  
  - [Spot Crime Map of Broadview](http://spotcrime.com/wa/seattle/broadview): This is cool. It looks like it is built from publically available data and APIs. It has some key features which are nice, these include (1) a data stream from community reporting (you can register and then report crimes) (2) customizeable email alerts (3) maps bounded out by neighborhood. The downside is all the advertising and clunkiness of some UI aspects. This does seem like a good model for an open app.
  
  - [SPD 911 Response Map](http://web6.seattle.gov/mnm/incidentresponse.aspx): As one may guess this is a map of SPD 911 responses.
  
  - [SPD Records Map](http://web6.seattle.gov/mnm/policereports.aspx): A map of police reports taken by officers responding to icidents around the city.  It takes about 12 hours after a report has processed for the  crime to show up.  Also, this is information from initial reports, so they may not match monthly crime stats. According to SPD this map will not provide a true measure of safety or crime in an area.
  
  - [SPD Crime Dashboard](http://www.seattle.gov/seattle-police-department/crime-data/crime-dashboard): A dashboard of crime stats which can be filtered by precinct, neighborhood (not all neighborhoods present), crime type etc. The dashboard is accompanied by a bar plot of count by month.
  
  - [San Francisco Crime Data Analysis](https://s3.amazonaws.com/andrei-iusan-ud-dand/P4_-_San_Francisco_Crimes_-_Andrei_Iusan.html): Exploratory data analysis project by a fellow Udacity student. This is very well done and the associated repo has some very useful code for analyzing and mapping crime data.
   
  - [Plotting and Predicting Seattle Crime](http://www.racketracer.com/2015/03/02/predicting-and-plotting-crime-in-seattle/): Self explanatory title, useful information here for plotting. The modeling is impressive too, just not as applicable for this project.
  
  - [Mapping Seattle Crime Density](http://www.racketracer.com/2015/03/14/mapping-crime-density-and-my-pre-crime-algorithm/): This is related to the link above.
  
  - [Most Frequented Crimes in SF by Neighborhood](http://www.racketracer.com/2015/10/19/most-frequented-crimes-in-san-francisco-normalized-by-neighborhood/): As you may have gleaned from the title, this resource contains tools and approaches for identifying and mapping the most frequent crimes in a specific geographic area, in this case SF neighborhoods. 
  
  - [Predicting Urban Crime in Diverse Settings](https://econ.duke.edu/uploads/assets/dje/2008/Fritz.pdf): Academic document of an early effort at crime prediction using SPD crime data and census data. A model was built using Seattle data. A generalized model was then applied to Durham NC. This document contains some useful tools and approaches for crime model building.  
  
  - [Tableau Vis of North Green Lake Crime](https://public.tableau.com/profile/dave.smith5366#!/vizhome/NorthGreenlakeCrime/Dashboard1): A nice visualization of crime in Greenlake by a Greenlake resident.
  
  - [Block Watch Toolkit](http://www.seattle.gov/police/blockwatch/toolkit.htm): Great list of online resources for block watch groups and individuals interested in adddressing and preventing crime in their neighborhoods. This includes links to data as well as the online crime reporting tool
  
  - [Community Online Reporting Program](http://www.seattle.gov/Police/report/default.htm): Online to tool to report crimes.
  
  - [Addressing Neighborhood Issues](http://www.seattle.gov/police/blockwatch/neighborhood.htm):  The City of Seattle has a lot of great resources for Seattle residents, but there is so much information available that sometimes it can be overwhelming. This page brings together many of the frequent issues that neighborhoods have to deal with all in one spot.  
  
  
  ### Selected Support Resources
  To meet our goals we need more than just crime data. At minimum it would be nice to have neighborhood boundary data, shapefiles, and demographic data.
  - TODO: insert resources

### TODO: Brainstorming of Ideas of things we can provide
- guiding principle should be tools or data packages that empower, enable action, and are maintainable.
- Basic explanation of crimes in general in Seattle
- crimes by neighborhood
- Top 5 or crimes that stand out for each neighborhood
- what crimes are occuring we can help prevent (e.g. mail theft, use lockboxes etc.)
- a data package for city officials or neighborhood organizations
- enhanced stats or visualizations to aid understanding about the data
- a reporting tool or mechnaism to build a data set of crimes not being reported to police ("petty crimes") or suspicious activities for which police may not be able to respond
- a mapping tool
- an alert tool
- a progress tool (are things getting better or worse by crime by neighborhood)
