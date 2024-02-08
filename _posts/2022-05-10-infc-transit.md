---
title: "Forecasting the Post-Pandemic Transit Recovery to Inform Relief Funding"
image: 
  path: /assets/images/projects/infc-transit/cover.jpeg
  thumbnail: /assets/images/projects/infc-transit/cover.jpeg
categories:
  - Prediction
tags:
  - infrastructure canada
  - canada
  - public transit
  - pandemic
  - covid-19
  - ridership
  - forecast
  - infrastructure
  - transportation
last_modified_at: 2024-01-25
---

As cities recover from the COVID-19 pandemic, there is a pressing need for fare-dependent transit agencies to have access to a reliable forecast of post-pandemic ridership recovery. I developed a machine learning-based forecast of this important metric for Infrastructure Canada.

# Project Overview

| **Motivation** | There is a pressing need for fare-dependent transit agencies to have access to a reliable forecast of post-pandemic ridership recovery |
| **Model** | A machine learning-based forecast of post-pandemic transit demand in major cities |
| **Client** | Infrastructure Canada (INFC) |
| **Status** | Complete |
| **Outcome** | Presented results to the Deputy Minister and supported \$14.9 billion in [Federal permanent public transit funding](https://www.infrastructure.gc.ca/transit-transport/index-eng.html) |

The COVID-19 pandemic has significantly affected public transit operations worldwide, with agencies experiencing up to [90% drops in ridership](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0242476) during initial lockdowns. Since then, ridership has remained substantially below pre-pandemic levels in most cities.

For transit systems that heavily depend on user fees for operational revenue, these ridership decreases [render pre-pandemic financing schemes unsustainable](https://trid.trb.org/view/1844009) and make transit dependent on external financing to maintain operations. Even as public health measures ease, the impact of the pandemic may have lingering effects on ridership that impose further financial burdens on public transit systems. Operators must plan for future dependence on external funding or alternative financing schemes until ridership returns to pre-pandemic levels.

As cities recover from the COVID-19 pandemic, there is a pressing need for fare-dependent transit agencies to have access to a reliable forecast of post-pandemic ridership recovery. Such a model would enable transit providers to understand the impact of various pandemic-related factors and predict the state of public transit use in the near future. 

This article walks through the creation of such a forecast using machine learning.

# Where does transit ridership data come from?

 **Public Transit Ridership**: The number of passengers using public transportation.
{: .notice} 

In order to understand the impacts of various pandemic-related factors on transit ridership, detailed public transit ridership data is needed. Changes in transit ridership can be difficult to ascertain at a granular level as most agencies only publish ridership figures at the monthly or yearly level. Data from third party sources, such as [Google's COVID-19 Community Mobility Reports](https://www.google.com/covid19/mobility/), can be used to fill these data gaps. 

The Community Mobility Reports provide daily data at the municipal or county level on changes in the number of visitors to transit stations compared to pre-pandemic levels. When adjusting for weekday variation, these reports offer a highly reliable and comparable approximation for transit ridership during the pandemic in different regions around the world.

Fifteen major cities in five different countries are chosen for analysis, providing a case study as to how specific pandemic policies and public health circumstances affected transit ridership.

![no-alignment]({{ '/assets/images/projects/infc-transit/ridership.png' | absolute_url }})

Data provided by these cities on COVID-19 cases, gathering restrictions, park closures, border closures, and changes in work-related traveling can be used to model impacts on transit ridership and forecast ridership recovery for the next two years. 

By creating predictions for the selected cities, ridership recovery trends can be better understood by local transit operations and generalizations can be made about ridership trends across all cities affected by the pandemic.

# How can transit ridership be forecasted?

The following variables are included in the model:

| Variable Name               | Definition                                                            |
|-----------------------------|-----------------------------------------------------------------------|
| `transit_demand`       | Change in visitors to transit stations compared to before the pandemic|
| `metric_initial_drop`  | Average drop in `transit_demand` in the first month of pandemic  |
| `lagged_month_average` | Average `transit_demand` in the previous calendar month          |
| `past_average_month`   | Cumulative average `transit_demand` until the current month start|
| `days_since_pandemic`  | Number of days since the pandemic began                               |
| `cases_total`          | Cumulative rate of COVID-19 cases since the pandemic began            |
| `work_from_home`       | Change in visitors to work places compared to before the pandemic     |
| `policy_parks`         | Whether or not the city had closed off public parks                   |
| `policy_emergency`     | Whether or not the city had a state of emergency declared             |
| `policy_border`        | Whether or not the country had a major border closure                 |
| `policy_gathering_low` | Whether or not the city had prohibited indoor gatherings of 50-1,000  |
| `policy_gathering_med` | Whether or not the city had prohibited indoor gatherings of 5-49      |
| `policy_gathering_hig` | Whether or not the city had prohibited indoor gatherings more than 5  |
| `emergency_length`     | Number of days a state of emergency was in effect                      |
| `gathering_low_length` | Number of days indoor gathering restrictions (50-1,000) were in effect|
| `gathering_med_length` | Number of days indoor gathering restrictions (5-49) were in effect    |
| `gathering_hig_length` | Number of days indoor gathering restrictions (<5) were in effect      |
| `lockdown_total`       | Total number of days indoor gatherings were prohibited during pandemic|

Where `transit_demand` is the variable that is targeted for prediction and the other variables are the predictors.

To forecast public transit ridership using these predictors, a [Random Forest regression](https://levelup.gitconnected.com/random-forest-regression-209c0f354c84) model was trained using the available sample data. The final model explains 99.77% of the variance in public transit ridership during the pandemic.

[Variable importance](https://www.displayr.com/how-is-variable-importance-calculated-for-a-random-forest/) can be extracted from the model to better understand which pandemic-related factors have the largest impact on transit ridership.

![no-alignment]({{ '/assets/images/projects/infc-transit/variable_importance.png' | absolute_url }})

Unsurprisingly, average ridership in the past month has the highest predictive value in the model. This is important for forecasting, as it means that future predictions are still be highly dependent on recent ridership levels. Similarly, the change in visitors to work places compared to before the pandemic is very important to the predictions. Total bans on gathering restrictions, the initial drop in transit ridership, and the cumulative number of COVID-19 cases are also relatively important in the model, but less so than past month ridership and workplace mobility.

In order to ensure that the model is not overfit to the data, a secondary model was trained on a sample of the data that excluded the most recent one hundred days. The next one hundred days were then forecasted using this model to produce an [ex-post forecast](https://ec.europa.eu/eurostat/statistics-explained/index.php?title=Glossary:Ex-post_forecast), giving an indication of how accurate the model will be in the future when applied to data outside of the training set.

This model is indeed very accurate, with a mean absolute error of 6.1%, meaning on average the predictions were ±6.1% off from the actual change in transit ridership compared to pre-pandemic levels. This implies that forecasted values will be reasonably accurate even when they extend beyond the time frame on which the model was trained.

# When will public transit ridership return to pre-pandemic levels?

To forecast transit ridership into the future, some assumptions need to be made. To keep things simple, it can be assumed that current pandemic circumstances will remain unchanged. This assumes that public health restrictions will not revert to serve levels seen in the past, and COVID-19 case rates will remain similar to the recent rates. The difference in the number of visitors to workplaces during the pandemic is also assumed to remain similar to recent levels. Thus, the forecast is conditional on these pandemic-related variables remaining constant during the prediction period.

Likewise, it has to be assumed that no policy interventions that impact public transit use will come into effect. These include programs to incentivize ridership, such as fare reductions, or actions that subsidize personal vehicle use, such as spending on new highways. 

With these variables held constant, the factors that affect the forecasted transit ridership are time-related, based on general recovery trends that the model separates from the effects of the other variables. There are also effects caused by interactions between time and other variables. For example, gathering restrictions might be expected to have less and less effect on transit ridership over time as [pandemic fatigue](https://wdgpublichealth.ca/blog/pandemic-fatigue-what-it-and-how-do-we-move-past-it) sets in. Finally, past levels of transit ridership impact the forecast as transit ridership is evidently highly correlated with recent ridership levels.

With these assumptions, a two-year forecast can be produced for the fifteen chosen cities:

![no-alignment]({{ '/assets/images/projects/infc-transit/forecast.png' | absolute_url }})

To simplify the results, we can look at the average forecasted ridership levels during each quarter of the next two years:

| City          | 2022-Q2 | 2022-Q3 | 2022-Q4 | 2023-Q1 | 2023-Q2 | 2023-Q3 | 2023-Q4 | 2024-Q1 | 2024-Q2 |
|---------------|-------- |---------|---------|---------|---------|---------|---------|---------|---------|
| Brisbane      | -35.8%  | -35.9%  | -36.6%  | -37.8%  | -37.7%  | -37.0%  | -37.0%  | -36.8%  | -36.5%  |
| Calgary       | -29.5%  | -29.6%  | -29.9%  | -29.9%  | -30.1%  | -31.3%  | -30.9%  | -31.0%  | -30.7%  |
| Chicago       | -31.3%  | -30.9%  | -31.0%  | -31.0%  | -30.9%  | -30.9%  | -30.8%  | -30.9%  | -31.1%  |
| Dallas        | -27.5%  | -29.6%  | -30.2%  | -29.3%  | -27.7%  | -27.4%  | -27.4%  | -27.4%  | -27.4%  |
| Houston       | -19.8%  | -19.8%  | -19.8%  | -19.8%  | -19.8%  | -20.0%  | -19.8%  | -19.9%  | -19.8%  |
| London        | -31.5%  | -29.5%  | -29.6%  | -29.8%  | -29.8%  | -27.8%  | -24.2%  | -23.9%  | -23.9%  |
| Montréal      | -29.4%  | -23.4%  | -20.8%  | -20.3%  | -20.4%  | -18.0%  | -17.2%  | -17.1%  | -17.1%  |
| New York      | -30.1%  | -30.4%  | -30.0%  | -29.6%  | -30.0%  | -29.8%  | -29.7%  | -29.8%  | -29.7%  |
| Paris         | -11.2%  | -16.2%  | -16.0%  | -13.5%  | -12.9%  | -12.8%  | -12.7%  | -12.6%  | -12.6%  |
| Philadelphia  | -40.9%  | -34.5%  | -29.8%  | -27.5%  | -20.7%  | -20.6%  | -20.5%  | -20.4%  | -20.4%  |
| Phoenix       | -24.4%  | -25.3%  | -23.7%  | -23.2%  | -23.1%  | -23.1%  | -22.9%  | -22.9%  | -23.0%  |
| San Antonio   | -28.2%  | -28.1%  | -26.8%  | -25.9%  | -25.8%  | -25.7%  | -25.8%  | -25.8%  | -25.9%  |
| San Diego     | -31.4%  | -31.2%  | -30.5%  | -30.5%  | -30.5%  | -30.4%  | -30.1%  | -30.0%  | -30.0%  |
| San Francisco | -44.7%  | -36.0%  | -36.3%  | -31.6%  | -29.7%  | -29.7%  | -29.6%  | -29.4%  | -29.4%  |
| Toronto       | -35.7%  | -27.7%  | -21.3%  | -20.3%  | -18.9%  | -18.9%  | -18.7%  | -18.7%  | -18.6%  |

Where the values in the table are the forecasted change in transit station visitors compared to the pre-pandemic baseline.

All the cities examined are forecasted to have ridership remain below pre-pandemic levels by May 2024, though some recovery is predicted during that time interval. Paris is predicted to have the best overall recovery by the end of the two years, while Brisbane is predicted to have the worst. Relative to current levels, Philadelphia is predicted to have the greatest absolute gains in ridership while Brisbane is predicted to have the smallest.

In general, the model shows that cities that still have pandemic measures in place or have only recently lifted restrictions are likely to see some recovery as public health measures continue to ease. Conversely, cities that have had measures lifted for a longer period of time have likely already realized most of the ridership gains from lifting restrictions

Overall, the forecast implies a "new normal" for transit ridership, with no full recovery in sight for at least the next two years. It is important that fare-dependent transit providers have access to such forecasts so that they can seek the appropriate funding structures to preserve operations until ridership fully recovers.


*All data and code for this analysis can be found [here](https://github.com/rapsoj/forecasting-transit-recovery).*
