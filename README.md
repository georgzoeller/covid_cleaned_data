# covid_cleaned_data
Cleaned / processed data from various public COVID-19 datasets in readily ingestible JSON format


## JHUSS Timeseries

Data based on [JHUSS timeseries](https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series) in various formats


1. /czml/timeseries.czml - Cases/Deaths/Recoveries time-series in [CZML](https://github.com/AnalyticalGraphicsInc/czml-writer/wiki/CZML-Guide).
 - Inclusive any changes from 2 
 - Recoveries are displayed as proportional to highest single report poly-lines and circles
 - Yellow to red color for hue shift based on proportions
 - Labels for Countries
 - Detailed descriptions for any available location for cases/deaths/recoveries and CFR
 
 ![Screenshot](https://github.com/georgzoeller/covid_cleaned_data/blob/master/Screenshot%202020-03-21%20at%2004.12.39.png?raw=true)


2. /json/jhuss_timeseries.json - Cases/Deaths/Recoveries time-series based on aggregated and cleaned as JSON object 

Transformation:
  - Forward filled Cases/Deaths/Recoveries per day meaning that cases no longer drop to 0 after they emerged due to lack of updates. This means points no longer disappear.
  - Currently locations are based on the confirmed table. There are inconsistencies in Long/Lat being different in Deaths and Recoveries.
  - Aggregated all 3 original timeseries into one.
  - Dropped all 0 case objects

Example:
```
[
 {
   "country":"Thailand",
   "name":"Thailand",
   "lat":15,
   "long":101,
   "confirmed":[2,3,5,7,8,8,14,14,14,19,19,19,19,25,25,25,25,32,32,32,33,33,33,33,33,34,35,35,35,35,35,35,35,35,37,40,40,41,42,42,43,43,43,47,48,50,50,50,53,59,70,75,82,114,147,177,212,272],
   "deaths":[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
   "recoveries":[0,0,0,0,2,2,5,5,5,5,5,5,5,5,5,5,5,10,10,10,10,10,12,12,12,14,15,15,15,15,17,17,21,21,22,22,22,28,28,28,31,31,31,31,31,31,31,31,33,34,34,35,35,35,35,41,42,42],
   "intervals":{"2020-01-21T16:00:00.000Z/2020-01-22T16:00:00.000Z":[2,0,0],
   "2020-01-22T16:00:00.000Z/2020-01-23T16:00:00.000Z":[3,0,0],
   "2020-01-23T16:00:00.000Z/2020-01-24T16:00:00.000Z":[5,0,0],
   "2020-01-24T16:00:00.000Z/2020-01-25T16:00:00.000Z":[7,0,0],
   "2020-01-25T16:00:00.000Z/2020-01-27T16:00:00.000Z":[8,0,2],
   "2020-01-27T16:00:00.000Z/2020-01-30T16:00:00.000Z":[14,0,5],
    ...
   },
   "total_confirmed":272,
   "first_confirmed":"2020-01-21T16:00:00.000Z",
   "total_deaths":1,
   "first_deaths":"2020-02-29T16:00:00.000Z",
   "total_recoveries":42,
   "first_recoveries":"2020-01-25T16:00:00.000Z"
 }
```

