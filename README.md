# WHO covid19 CSV reports data + PDF parser

Parse WHO covid19 PDF reports, and provide data by country in CSV format.
This repository provides the extracted CSV data (starting from march 1, 2020) + the parser source code.

**Latest parsed data (CSV) are here: [data/csv](data/csv)** . Note that files are named against their date of publication + report #, and the date corresponds to data collected the day before (eg. 20200322-sitrep-62-covid-19.csv contains data as of march 21, and is report #62). Same naming convention as WHO reports.

WHO reports available here:
https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports

Parser should not work for reports published before March 2, 2020 (data as of march 1st).

## Why are data important ?

Data can help people discover new things. They can be related to epidemiology (refine knowledge about how the virus spreads, when, where, for how long...), but may also help new ideas to emerge (correlate virus spread with external factors, like pollution, sociological facts, economy... by using other available data sources).

The more exploitable data sources are available, the more public, private or individual researchers, statisticians, data scientists or even journalists can easily get material to work.

Open data is certainly a key driver of future social progress, knowledge, freedom, and democracy.

## Are there other data sources ?

Among data sources available, I would recommend these ones:
- Johns Hopkins University (USA): https://github.com/CSSEGISandData/COVID-19 (CSV format, with daily data and time series).
- ECDC (European Center for Disease Control): https://www.ecdc.europa.eu/en/publications-data/download-todays-data-geographic-distribution-covid-19-cases-worldwide (Excel format + import script for R language).
- https://github.com/covid19-data/covid19-data provides aggregates from multiple datasets, including ECDC and WHO (CSV + JSON formats).

## Parser quick start

Read this only if you need to parse the WHO data yourself: for example, if you don't trust my data, or if I fail to provide data in the coming days :)

### Build:
```
mvn clean install
```

### Execute:

```
java -jar target/whocovid19-0.0.1-SNAPSHOT.jar <options>
```

Options can be:
* No option: parses /tmp/report.pdf and outputs to console.
* PDF report file name: parses report and outputs to console.
* sourceDirectory targetDirectory: parses all PDF files present in source dir, then outputs CSV in target dir (created if needed). File names are rpeserved (except extension, ".csv" instead of ".pdf").

### Examples:

Parse WHO march 19 PDF report:
```
java -jar target/whocovid19-0.0.1-SNAPSHOT.jar 20200319-sitrep-59-covid-19.pdf
```

Parse all reports in ~/who-reports directory, and place results in /tmp/results:
```
java -jar target/whocovid19-0.0.1-SNAPSHOT.jar ~/who-reports /tmp/results
```

### Output:

CSV data should be generated, looking like this (generated from march 4, 2020 report):

```
Country,Confirmed cases,New cases,Deaths,New deaths,Transmission type,Days since last case
Republic of Korea,5328,516,32,4,Local transmission,0
Japan,284,16,6,0,Local transmission,0
Singapore,110,2,0,0,Local transmission,0
Malaysia,50,21,0,0,Local transmission,0
Australia,43,10,1,0,Local transmission,0
Viet Nam,16,0,0,0,Local transmission,20
Philippines,3,0,1,0,Imported cases only,28
New Zealand,2,0,0,0,Imported cases only,1
Cambodia,1,0,0,0,Imported cases only,36
Italy,2502,466,80,28,Local transmission,0
France,212,21,4,1,Local transmission,0
Germany,196,39,0,0,Local transmission,0
Spain,151,37,0,0,Local transmission,0
the United Kingdom,51,12,0,0,Local transmission,0
Switzerland,37,7,0,0,Local transmission,0
Norway,33,7,0,0,Local transmission,0
Netherlands,28,10,0,0,Local transmission,0
Austria,24,6,0,0,Imported cases only,0
Sweden,24,9,0,0,Local transmission,0
Iceland,16,7,0,0,Imported cases only,0
Israel,12,2,0,0,Local transmission,0
Croatia,9,1,0,0,Local transmission,0
Belgium,8,0,0,0,Imported cases only,1
Denmark,8,3,0,0,Local transmission,0
San Marino,8,0,0,0,Local transmission,1
Finland,7,0,0,0,Local transmission,1
Greece,7,0,0,0,Local transmission,2
Czechia,5,2,0,0,Imported cases only,0
Romania,4,1,0,0,Local transmission,0
Azerbaijan,3,0,0,0,Imported cases only,3
Georgia,3,0,0,0,Imported cases only,3
Russian Federation,3,0,0,0,Imported cases only,1
Estonia,2,1,0,0,Imported cases only,0
Ireland,2,1,0,0,Imported cases only,0
Portugal,2,0,0,0,Imported cases only,1
Andorra,1,0,0,0,Imported cases only,1
Armenia,1,0,0,0,Imported cases only,2
Belarus,1,0,0,0,Imported cases only,5
Latvia,1,0,0,0,Imported cases only,1
Lithuania,1,0,0,0,Imported cases only,5
Luxembourg,1,0,0,0,Imported cases only,2
Monaco,1,0,0,0,Under investigation,3
North Macedonia,1,0,0,0,Imported cases only,6
Poland,1,1,0,0,Imported cases only,0
Ukraine,1,1,0,0,Imported cases only,0
Thailand,43,0,1,0,Local transmission,1
India,6,1,0,0,Imported cases only,0
Indonesia,2,0,0,0,Local transmission,2
Nepal,1,0,0,0,Imported cases only,40
Sri Lanka,1,0,0,0,Imported cases only,37
Iran (Islamic Republic of),2336,835,77,11,Local transmission,0
Kuwait,56,0,0,0,Imported cases only,2
Bahrain,49,0,0,0,Imported cases only,1
Iraq,31,5,0,0,Imported cases only,0
United Arab Emirates,27,6,0,0,Local transmission,0
Lebanon,13,0,0,0,Local transmission,1
Oman,12,6,0,0,Imported cases only,0
Qatar,8,1,0,0,Imported cases only,0
Pakistan,5,0,0,0,Imported cases only,1
Egypt,2,0,0,0,Imported cases only,2
Afghanistan,1,0,0,0,Imported cases only,8
Jordan,1,0,0,0,Imported cases only,1
Morocco,1,0,0,0,Imported cases only,1
Saudi Arabia,1,0,0,0,Imported cases only,1
Tunisia,1,0,0,0,Imported cases only,1
the United States,108,44,6,4,Local transmission,0
Canada,30,3,0,0,Local transmission,0
Ecuador,7,1,0,0,Local transmission,0
Mexico,5,0,0,0,Imported cases only,2
Brazil,2,0,0,0,Imported cases only,3
Argentina,1,1,0,0,Imported cases only,0
Chile,1,1,0,0,Imported cases only,0
Dominican Republic,1,0,0,0,Imported cases only,2
Algeria,5,0,0,0,Local transmission,1
Nigeria,1,0,0,0,Imported cases only,5
Senegal,1,0,0,0,Imported cases only,1
International conveyance (Diamond Princess),706,0,6,0,Local transmission,2
Grand total,12669,2103,214,48,n/a,n/a
China,80422,120,2984,38,Under investigation,0
```

