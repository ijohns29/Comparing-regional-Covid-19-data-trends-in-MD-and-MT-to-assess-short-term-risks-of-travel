# Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel
Comparing regional Covid-19 data from these two locations to assess risks of travel to and from. 
## __Isaac Johnson__ 
### __Mini Project #1 - Data Trends and Visualization with Python__
### Decision Analytics
### EN.663.667 (02)
### 2020.12.03

# Background
Covid-19 virus is strongly speculated to have origins from China and transferred to humans in 2019. Due to global interconnectivity in world today and lack of government action the local outbreak in China quickly became a worldwide pandemic. The US in particular has experienced bad outbreaks due to variety of reasons e.g. lax travel restrictions in the early months of the pandemic, lack of monitoring for symptoms of incoming people, lack of testing or PPE production during the early deays of the pandemic, and lack of coordinated federal response of US govt towards Covid-19. Additionally, mixed messaging and politicization of practical safety measures exacerbated the spread of the virus, as well as peoples general indifference toward something not directly impacting them. Throughout the year Covid-19 has been unable to be contained with each surge stronger than the last. The baseline heading into the fall was deemed quite high, about 4x higher than preferred levels, and widespread community transmission is now seen in almost all areas of the USA during late autumn/winter season. Due to these conditions its possible many companies or local governments are looking at strongly suggesting or limiting travel during the upcoming winter holidays e.g. Thanksgiving and Christmas/New Years. While some local governments strongly suggested not traveling for Thanksgiving there was no enforcement of this policy thus many peopel did travel home. Therfore it's even more prudent to monitor current Covid-19 trends be aware of current guidelines for travel, testing, quarantining etc and try to anticipate impacts on future activities.

# Business Question
__What are recent Covid-19 virus data trends in regions of travel (Maryland and Montana) and what impact might these have on planned business travel?__

# Data Question - Open Data
Data may come from the below sources:
1. __New York Times Covid-19 Data - US Counties and States__: The New York Times provides Covid-19 data, both live and historical, for the Covid-19 epidemic occuring within the USA + territories during year 2020. Data is available on national, state and county level and available data has been tracked since the epidemic started in January. This data comes from reports from state and local health agencies. Due to shortages of tests that were available the data may not reflect full extent of epidemic.
  i. The data used will be historical data. This data does not include results from current day but does include results up to current day. There will be no distinction made between probable cases and/or lab confirmed cases. 
2. __Press releases from state and local authorities__: These posts will be sourced from government websites or local websites where the executive orders or briefings are made available. The City of Baltimore Executive orders can be found [here](https://www.baltimorecity.gov/executive-orders), Maryland state press briefings can be found [here](https://governor.maryland.gov/coronavirus/), updates on status of reopening in Montana can be found [here](https://covid19.mt.gov/joint-information-center), and information on Butte, MT can be found at county level by looking at Silverbow county data [here](https://www.co.silverbow.mt.us/2167/COVID-19).
3. __Technical Definitions__:The data is organized geographically by Federal Information Processing Standards [FIPS](https://www.census.gov/library/reference/code-lists/ansi/ansi-codes-for-states.html) State Numeric Codes. In this case we are concerned with Maryland (FIPS - 24) and Montana (FIPS - 30). [County level](https://www.nrcs.usda.gov/wps/portal/nrcs/detail/national/home/?cid=nrcs143_013697) FIPS data is available here. This allows the analyst to look at specific regions of travel e.g. Baltimore City (considered county equivalent), Silverbow County (Butte, MT).
4. The original files can be accessed on google drive [here](https://drive.google.com/drive/folders/1yKs4EpQ-lBj622hN-uQh5lPIDsdcVdiz?usp=sharing), and the edited files can be found [here](https://drive.google.com/drive/folders/1LyowVM_9O5uZdNPDw40N82UA0UU1BN_G?usp=sharing). Links are open access. 

# Data Question - Analysis
Python and Google Collaboratory will be used for data analysis
- __What has the previous month's trend been in terms of covid cases?__ This will look at daily cases at state level to see whether the region is entering danger zone and look at daily cases, 3-day-average,and [incidence](https://www.cdc.gov/coronavirus/2019-ncov/downloads/global-covid-19/SARS-CoV-2-Transmission-Metrics.pdf) defined as "the occurence of new cases of a disease over a specified period of time" and mathematically defined as ((number of new cases of disease during specified period)/(by size of population at start of period)) * 100,000 gives you cases per 100,000 population. By using incidence can compare different regions. The population size is based on census data last taken in 2010 found here for [Montana](https://www.census.gov/prod/cen2010/cph-2-28.pdf), [Maryland](https://www.census.gov/prod/cen2010/cph-2-22.pdf). The data from NYT is reported in terms of __cumulative__ cases so daily difference must be taken to get daily new cases. Sometimes a person is later reclassified to different county, state etc so this explains a decrease in cumulative cases over time that may occur throughout data. An alternative is to consider [incidence rate](https://www.cdc.gov/csels/dsepd/ss1978/lesson3/section2.html) but that assumes that probability of disease is constant. Given the flux of people through all areas of USA this doesn't seem like a valid metric to use as risk increases with higher population densities and other factors e.g. age, state of immune system etc.
- __What is the previous month's trend for deaths?__ This will look at daily reported deaths, 3-day-average, and 3-day-incidence to provide idea about whether state/county health agencies are in danger of being overwhelemed.The Department of Health and Human Services (HHS) provides state level data on this [here](https://healthdata.gov/dataset/covid-19-estimated-patient-impact-and-hospital-capacity-state). 
- __What have been the previous month's recommendations from Governor or Mayor?__ This will provide an idea of how proactive government agencies are being at handling pandemic and allow for travel/post travel plans to be made so that the spread of Covid-19 can be limited and travel can be conducted safely or with minimized risk.

# Data Answer
## Trends in daily covid cases
First the daily covid cases for past 30 days were examined for Maryland and Montana. This provides some surveillance of the landscape we're going to potentially be interacting with. Maryland and Montana have vastly different population sizes with Maryland population estimated as 6 million while Montana population is estimated as ~ 1 million. Th land masses are also quite different with Maryland being about 8.5% the size of Montana indicating high differences in population density.
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Figure_1_Covid19_daily_cases_MD.jpg)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Figure_2_Covid19_daily_cases_MT.jpg)

Secondly, we examined 3-day average trend and 3-day incidence. According to the CDC, the 3-day incidence number can be used to determine whether illnesses in the area are increasing, decreasing, or stable. Depending on the incidence level its possible to know the threat level of the region with [classifications](https://ethics.harvard.edu/files/center-for-ethics/files/key_metrics_and_indicators_v4.pdf) as follows: green (< 1 daily new case per 100k), yellow (< 10 daily new case per 100k), orange (10<25 daily new case per 100k), and red (> 25 daily new case per 100k). As one can see average cases per 100 k have risen significantly in both locations over the course of the last month. While Baltimore has experienced more a rising plateau, the outbreak in Silver Bow county is much more severe and illnesses are increasing rapidly. 
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Figure_3_Covid19_daily_cases_MD_avg.jpg)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Figure_4_Covid19_3_day_incidence_MD.jpg)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Figure5_3_day_avg_cases_MT.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Figure6_3_day_incidence_MT.png)

## Trends in 3 day average of deaths
The 3  day death rate for Maryland and Montana are shown below in Figure 7-10. Figure 7 and 8 show the data for Maryland as a 3-day average and normalized for population, similar data is shown in Figure 9 and 10 for Montana. During the month of November the death rate has steadily risen. There was a dip in the later part of the month, this is attributed to the a decrease in testing due to national holiday. In Silver Bow county there were essentially no deaths throughout October. However, as incidence began rising in October, this has lead to the death rate creeping up during the beginning of November. Given that cases per 100k are still rising there the death rate is expected to rise further. Additionally, Montana is a sparsely populated state. It does not have comparable resources to Maryland. Standards of care are likely to fall as cases rise, leading to more deaths, and the hospital bed ICU system has a much lower capacity compared to Maryland.
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig7_3day_deaths_MD.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig8_3day_death_incidence_MD.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig9_3day_deaths_MT.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig10_3day_death_incidence_MT.png)

## Occupancy of Beds in Hospitals for Maryland and Montana
Here we can see recent trends in hospitalizations for these two states. In terms of total beds occupied the ratios have remained relatively constant over the past month with Montana percentage about 60-70% while Maryland is steady 80%. While Maryland does have a higher occupancy rate than Montana, it could be do to variety of reasons e.g. more elective procedures. Both states also have high percentage of ICU beds currently occupied however Montana hospitals seem to have seen an increase of about 10-15% over the past month. This could be partly attributed to rise in Covid-19 cases or perhaps weather related incidents as the temperatures have fallen there recently. Lastly, we look at occupancy of ICU beds as percentage of Covid-19 afflicted patients. Both currently have relatively low percentage of beds occupied by covid-19 patients, however these patients typically require significant amounts of care and occupy the ICU beds for longer times than traditional ICU patients. Both states have seen a rise of about 4-5% in Covid-19 bed usage over the past month. Care should be taken to reduce the rising number of cases incoming lest the hospital system be overwhelmed. While remaining hospital beds can be converted to ICU beds there are staff concerns and potentially eventually space concerns. Additionally, as the US experiences widespread outbreaks throughout the nation, rather than the regional ones previously seen, it becomes much more difficult to send workers to places that need surge capacity.      
![alt text](https://github.com/ijohns29/Baltimore-Butte-comparing-covid-19-data/blob/main/Figure5%20Inpatient%20Beds%20in%20Hospital.jpg)
![alt text](https://github.com/ijohns29/Baltimore-Butte-comparing-covid-19-data/blob/main/Figure6%20Inpatient%20ICU%20Beds%20in%20Hospital.jpg)
![alt text](https://github.com/ijohns29/Baltimore-Butte-comparing-covid-19-data/blob/main/Figure7%20Inpatient%20ICU%20Beds%20in%20Hospital%20Occupied%20with%20Covid%20Patients.jpg)
![alt text]()
![alt text]()

## Airport Safety Precautions
1. Currently BWI airport has a number of administrative controls in [place](https://www.bwiairport.com/COVID19socialdistancing) to minimize spread of Covid-19. These include all restuarants at 50% capacity, social distancing and masks required, as well as various plexiglass installments at high traffic areas (e.g. security, airline counters, checkout lines etc.). Currently the government of the state of Maryland, and posted on the BWI [airport](https://www.bwiairport.com/COVID19socialdistancing) strongly discourages travel to areas with incidence equal to or greater than 20 per 100k. 
2. The [ATL](https://www.atl.com/COVID19/) airport seems to have less restrictions in place. Face masks, signage and increased cleaning are part of their mitigation efforts however there was no mention of plexiglass controls or reduced restaurant capacity.\
3. [SLC](https://slcairport.com/customer-assistance/travel-advisory-2/) had similar restrictions as BWI and mentioned use of touchless restroom controls. 
4. [BTM](https://co.silverbow.mt.us/2167/COVID-19) listed basic conditions such as mask wearing and hygiene but no other engineering controls were mentioned. They did include latest update on local Covid-19 status, local restrictions in place and most recent state goal i.e. getting 7 day incidence below 25 per 100k for two weeks.
The [Maryland Department of Health](https://phpa.health.maryland.gov/Documents/2020.11.10.03_MDH_Advisory_Large_Gatherings_Travel_Long_Term_Care_Visitation.pdf) recently issued guidance for travelers from Maryland. They recommended all Maryland residents returning from out of state get tested for Covid-19 within 72 hours of their departure from their out of state destination. Furthermore it is recommended they quarantine while awaiting their test results. Secondly, any Marylander who travels to state with Covid-19 rate greater than or equal to 20 per 100k (in past 7 days of their visit) should be tested and quaratine at home until results have been received.  
# Business Answer
Using this data analysis the company personnel can examine regional trends regarding Covid-19 outbreak and assess the level of risk that the employee may be subjecting themselves to during their travel. The manager should be aware this data analysis may not indicate emerging outbreaks as these tend to flare up suddenly. Furthermore this assessment does not make any assumptions regarding employee behavior during travel, which will likely be the largest factor that will impact Covid-19 risk. It's recommended that travel be approved or rejected based on trends and local guidance and then reassessed within one week of departure date to see how the outbreak has evolved and plans adjusted accordingly. Organizational guidance regarding holiday travel can be found [here](https://hub.jhu.edu/2020/10/20/covid-19-winter-holidays/?mc_cid=295c6bc1e2&mc_eid=4aff72f931). Based on available data presented above travel is strongly discouraged to Silver Bow county as Covid-19 incidence is in red zone for both departure and arrival cities, and hospital capacity appears limited in both states. Should travel occur the indivual should test before leaving and after arrival to destination, as well as upon return. The individual should quarantine at residence until results of testing are known. 
With regards to improvements that could be made it'd be better if new data fed into it more smoothly. Right now I'd have to manually import everything and then tweak graphs. In future I'd prefer to update with positivity rate as I think that's a little more intuitive to understand than incidence. Future data visualizations could be more beautiful or have maybe a 3D aspect. Outbreaks aren't that predictable, but it'd be nice if you could estimate out to the expected travel dates. I based a lot of data on local locations but typically travel restrictions gear more towards the state as a whole. I still believe its useful to know the local situation and plan accordingly though. Breakdown of Covid infections/deaths by age would be useful to include and perhaps general data on ICU bed occupancy reason beyond Covid. 
