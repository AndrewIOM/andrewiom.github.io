---
layout: post
title:  "Isle of Man Population Projections: an Uncertainty Estimate"
date:   2019-08-22 10:00:00 +0000
tags: 
    - Isle of Man
    - Modelling
    - Population Growth
thumbnail: "/media/douglas.jpg"
thumbnail_caption: "Douglas, Isle of Man"
---

The Island’s housing need relies on accurate and up-to-date population statistics and projections. Government have committed to using the latest demographic information for the Area Plan process in the Strategic Plan. However, Government’s latest housing need figure does not take into account new observational data that was released as part of the 2016 census. Government’s population projections are also deterministic and do not therefore quantify uncertainty arising from assumptions about population change and measurement error in the Isle of Man datasets. It is desirable to quantify uncertainty to be sure that the precautionary principle is respected when used in land-use planning terms. The United Nations have adopted a Bayesian approach that applies hierarchical models to estimate Total Fertility Rate (TFR), life expectancy, and future populations, all with model uncertainty (Raftery et al 2014). This approach uses the same underlying intercensal compartment approach that is used in the official Isle of Man Government projections, but properly accounting for uncertainty. Here, I apply the latest UN method using the latest publicly available information to create population projections and show the bounds of uncertainty.

* Note: I'll update this post shortly with the full input data and original data sources in due course.*

## Method

I collated historic datasets on Isle of Man demographics and integrated these into the United Nation’s global hierarchical population model. I conducted analysis using the UN-authored R package bayesPop (Ševčíková and Raferty 2016), which allows the implementation of thr UN modelling approach with additional data sources. The following inputs were required for the model: age- and gender-specific population counts, death rates, and fertility rates as a percentage of the total fertility rate; and projections of future sex ratio and age/gender-specific migration. I compiled a number of datasets from Government sources. Age- and sex-specific population structure for each census period was determined from census reports and academic publications (Kelly 1999). Due to lack of publicly available information in the Isle of Man, I used UK average age- and sex-specific mortality rates within the model. 

Total Fertility Rate (TFR) was estimated with uncertainty by fitting a global hierarchical model to the United Nations global population projections dataset that was extended with Isle of Man TFR data obtained from Government reports (Alkema et al 2011, Fosdick and Raftery 2014). Similarly, uncertainty-based projections of male and female life expectancy were estimated from 1980-present Isle of Man life expectancy data (Chunn et al 2013). The predicted life expectancy and TFR were provided as inputs to the probabilistic population model. I used the same future projections of migration as the Government in their projections: zero, 500 and 1000 net migration based on the 2006 – 2016 age- and sex-related migration trend. Projections were calculated to 2100 but are truncated to 2040 in this post.

## Result: Population Projections with Uncertainty

The probabilistic population projections were broadly similar to the Government’s population projections (see below graphs). From the 2016 population total of 83,314, my median prediction to 2038 under zero migration predicts less of a decline in population than the official Government projection to 2036. 

![](/media/iom-pop-projection-zero-migration.png)
![](/media/iom-pop-projection-500-migration.png)
![](/media/iom-pop-projection-1000-migration.png)
*Isle of Man projected population using deterministic future migration scenarios that are the same as the Isle of Man Government’s projections (Top = zero migration; middle = net 500 migration, bottom = net 1000 migration). The 95% Prediction Intervals (PI) represent the region in which we can be 95% confident of the projection given previous observations.*

I also created another projection using a crude migration scenario where the age- and sex-related migration trend into the future is the same as the 40-year average (from 1976 - 2016). This probably isn't realistic given the Island's current economic conditions:

![](/media/iom-pop-projection-40y-trend.jpg)
*Isle of Man population projection based on the age- and sex-specific 1976-2016 migration trend.*

The mean net migration rate to the Island from 1976 to 2016 was 480 people per year. This is similar to the Government's current target of 500 per annum. However, the age-distribution is very different between the 2006-2016 and 1976-2016 means. 

## Implications for land-use planning and the ‘Area Plan for the East’

The 95% prediction intervals indicate uncertainty for population change for different migration scenarios. I suggest that the Area Plan should be refined to account for a median population prediction until 2026, with strategic reserves only allocated for the difference between the median projection and the upper 95% prediction interval. The complexity, however, lies in the assumption about the rate of future migration. 

In the next post, I'll be assessing the most appropriate future migration trend in light of demographic versus pension problems. 

## References

L. Alkema, A. E. Raftery, P. Gerland, S. J. Clark, F. Pelletier, Buettner, T., Heilig, G.K. (2011). Probabilistic Projections of the Total Fertility Rate for All Countries. Demography, Vol. 48, 815-839.

Fosdick, B., Raftery, A.E. (2014). Regional Probabilistic Fertility Forecasting by Modeling Between-Country Correlations. Demographic Research, Vol. 30, 1011-1034.

J. L. Chunn, A. E. Raftery, P. Gerland, H. Sevcikova (2013): Bayesian Probabilistic Projections of Life Expectancy for All Countries. Demography 50(3):777-801. doi:10.1007/s13524-012-0193-x

Kelly (1999), The demographic implications of economic growth in the Isle of Man. Population and the Environment.

Raftery, A.E., Alkema, L. and Gerland, P. (2014). Bayesian Population Projections for the United Nations. Statistical Science, Vol. 29, 58-68.
