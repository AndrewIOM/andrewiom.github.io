---
layout: post
title:  "Visualising climate model ensemble outputs in D3.js"
date:   2015-11-21 10:36:17 +0000
tags:
    - Future Climate
    - d3.js
---

Recently I was tasked with prsenting data for future climates to a diverse user base (public, professional, and scientific). It took a lot of time to understand how best to summarise complex outputs of global climate models, and how to display this information in an easy to understand format to end users of our software.

I found some great visualisations of climate ensemble statistics at the [Climate Service Centre Germany], and thought these would look good in our climate data interface to highlight the differences between emissions scenarios.  

<link rel="stylesheet" href="/projects/gcm-graphs/style.css">

# Isle of Man: Projected Mean July Temperatures
<div id="gcm-graph"></div>

On the left panel of this figure, the light grey area represents the likely range of mean July air temperature (10m above ground). The darker grey area represents the very likely range of future temperatures. 
The coloured lines indicate the ensemble medians for the various emissions scenarios (RCP2.6, 4.5, 6.0 and 8.5). 

The right panel is designed to highlight how the ensemble medians differ through time. In the near future, the predicted values are very similar, but as time progresses the high emissions scenario develops a larger range and median temperature. 

While I was working at Microsoft, I developed an Azure-powered system that collected the latest climate model outputs, created summary statistics and presented these in FetchClimate. This data was pulled from the datasets that I produced.

Check out the source code for this graph at [my GitHub repo].

<script src="https://code.jquery.com/jquery-2.2.0.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.6/d3.min.js" charset="utf-8"></script>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="/projects/gcm-graphs/app.js"></script>

[Climate Service Centre Germany]: http://www.climate-service-center.de/imperia/md/content/csc/projekte/csc-report13_englisch_final-mit_umschlag.pdf
[my GitHub repo]: http://github.com/AndrewIOM