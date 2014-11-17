Fare Evasion Data
=================

In April 2013, I filed a [FOIA request](https://www.muckrock.com/foi/new-york-city-17/fare-evasion-data-4975/) for data on fare evasion arrests in 2012. My request was bounced from the MTA to the NYPD, rejected, and then approved on appeal. For $17.50, I received 70 printed pages of tables. I was told that there was no way I would be able to get this data as a digital file. Which, okay. 

Since then I've been filing requests every three months to get basically "quarterly reports" of fare evasion arrests. They return it in bascially a differently formatted PDF each time. Because they can. 

I'm working on making this data machine-readable and available for people to use, and it would be cool if other people helped.

##Files

`2013` and `2014` should be self-explanatory. 

Original scanned PDFs (thanks to Dave Riordan for scanning and OCR-ing the 2013 data) are in the `pdf` folder. 2013 PDFs are separated by aggregation type, 2014 just has single files. 

Data-fied versions are currently going into the `csv` folder. I used [Tabula](tabula.nerdpower.org) to csv-ify the `fare-age.pdf` file and the `fare-gender.pdf` file. 

##Data Structure

There are 3 categories of data I requested: arrests by age, by gender, and by race. The data were given in aggregate. This is kind of annoying since it offers only flat analyses: we know how many 19-24-year-olds were arrested, and how many Hispanic people were arrested, and how many females were arrested, but not how many of those 19-24-year-olds were Hispanic or female. It's nowhere near as rich as Stop, Question, and Frisk (SQF) data. 

###2013
In each dataset, the arrests are organized by what appears to be **station entrance** rather than stations in total. Most of these are listed as cross-streets, with "&&" instead of "&". For example, there's a MANHATTAN AVENUE && NASSAU AVENUE-BROOKLYN entry and a NASSAU AVENUE && MANHATTAN AVENUE-BROOKLYN for the Nassau G stop. 

I am not sure if the naming convention can helpfully indicate which station entrance it refers to (especially since Nassau has, according to the city's [dataset of station entrances](https://data.cityofnewyork.us/Transportation/Subway-Entrances/drex-xx56), *six* entrances, two of which are actually at Manhattan Avenue & (or &&) *Norman* Avenue). 

Right now I'm thinking it makes the most sense to geocode all the rows of data, then aggregate those rows based on either *proximity* to each other (faster code-y solution) or based on just *verifying* stations that are part of the same system (solution that is more time consuming but accounts for stations that have really spread-out entrances, like the Union Square station which has 12 entrances across 3 city blocks (and 7 entries in the FOIA data)). Totally welcome other ideas. 
