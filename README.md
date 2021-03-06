# Final-BI-Project-COVID_19

Methodology :

This interactive feature aggregates data from the Johns Hopkins University Center for Systems Science and Engineering (JHU CSSE). Also, Supported by ESRI Living Atlas Team and the Johns Hopkins University Applied Physics Lab (JHU APL).

Report Overview:

This report, Covid-19-BI-Project is published on a daily basis. It relies entirely on open-source data; links to data sources are available on this page. As new data sources become available and new perspectives developed to understand the pandemic, the report will continue to evolve. It is a work in progress. Any ideas or suggestions, as well as comments on functionality, are welcomed. The report is a personal endeavor and not associated with any business or public entity. Because of the frequency of data updated, they may not reflect the exact numbers reported by governments organizations. Data updated through October 8,2021.

Accessing the Report:

The report is viewable on Microsoft's Power BI where the PBIX is also available for download. For example herewith the Country page picture.
![image](https://user-images.githubusercontent.com/90701842/141803298-078a3725-37b7-419c-a382-8fec1368ba03.png)

Inclusion of these data sources enables a number of informative calculations, such as Daily Cases, Dayly Deaths and the Number of Hospital Beds within a country.
For example Daily Cases  calculation:

Daily cases = 
VAR __CountryName = 'COVID'[Country]

VAR __State = 'COVID'[State]

VAR __Yesterday =  DATEADD(COVID[Date],-1,DAY)

VAR __TodaysCases = 'COVID'[Cases]


RETURN  __TodaysCases - CALCULATE(
    SUM('COVID'[Cases]) , 
    FILTER(
        COVID, 
        COVID[Date] = __Yesterday &&
        COVID[Country]  = __CountryName &&
        COVID[State] = __State
    )
) + 0


Refreshing the PBIX:

All the tables require refresh. They are accessed using the 'Web' connector and are available for anyone to refresh. When refreshing, I suggest using right clicking the COVID and Date tables in the Field Pane and refreshing each individually.

Prediction Model:

The Prediction model predicts Confirmed Cases  and Worldwide Mortality Rate at the date level. The model is similar to the one published by Kaggle (https://www.kaggle.com/therealcyberlord/coronavirus-covid-19-visualization-prediction).

This model is intended for planning treatment of confirmed cases. Underlying assumptions for the model will change over time as more data becomes available.

Links to data sources:

https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv

https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_deaths_global.csv

https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_daily_reports/11-07-2021.csv


Thanks:

Thanks to Shay Guri , our teacher for BI Course in INT College, Tel Aviv Israel, for his help in creating this metric for Power BI.

About the Author:

Tova Chen is the Economist at Rishon Le Zion Municipality, Israel. Tova studied Power Bi and Machine Learning to enhance her mind with a knowledge and to support and improve her work. Prior to joining Rishon Le Zion Municipality, Tova was a Economist at IAI, Finance Department. She received a B.A. from Bar Ilan University .

Contact:

Reach Tova at tchen1805@gmail.com
