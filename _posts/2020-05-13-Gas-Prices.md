---
layout: post
title: U.S. Gas Prices
subtitle: Forecasting Gas Prices using time-series analysis
image: https://www.moneycrashers.com/wp-content/uploads/2013/07/truth-about-gas-prices-1068x713.jpg
tags: [predictive, data analysis, gas, time-series]
---

As a small part of my labs project, I am doing some analysis on U.S. gas prices. Here is my current tableau graph!

[Tableau link](https://public.tableau.com/views/USGasprices/Dashboard1?:display_count=y&publish=yes&:origin=viz_share_link)
<center><iframe src="https://public.tableau.com/views/USGasprices/Dashboard1?:showVizHome=no&:embed=true" width="1024" height="768" frameborder="0"></iframe></center>

###### Note: embedding tableau was quite finnicky, the parameters ":showVizHome=no&:embed=true" was needed at the end.

My notebook on the preliminary modeling can be found [here](https://colab.research.google.com/drive/1C-n-fWukE0JJ0DKS2JRkI8Vefg2IvKdX#scrollTo=U6WAGO21KwwJ)

it includes a basic ARIMA model (1,1,0) as per a paper on predicting gas prices [here](https://www.researchgate.net/publication/328765225_Time-Series_Forecasting_Models_for_Gasoline_Prices_in_China)
