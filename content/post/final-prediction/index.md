---
title: Final Prediction
author: ''
date: ''
slug: []
categories: []
tags: []
---











# Introduction
In this week's blog, I present my final prediction model for the 2022 House Midterms. My final prediction model is a linear regression model using data from 1950-2020 to then predict the results in the House of Representatives for 2022. I predict that the **Democrats will win 207 seats**, while the **Republicans will win 223 seats**, resulting in a Republican victory in the House of Representatives. 

# Model Justification

The main inspiration from my model came from the article “Will Democrats Catch a Wave? The Generic Ballot Model and the 2018 US House Elections” by Alan I. Abramowitz (2018). This article discusses how one model that took in only three variables resulted in variables with high significance. These variables were: 1) the number of seats a party held before the given election, 2) whether the president’s party was Democrat or Republican, and the party’s lead or deficit on the generic ballot immediately after Labor Day. Although this was done for the Republican party, I gathered that the same could be applied to the Democrats.

Additionally, Gelman and King (1993) found that the closer it is to election day, the more accurate the polls are. This could be why the generic ballot variable used by Abramowitz (2018) also took into account only the results after Labor Day. Given this information, I filter the generic ballot polling data to only include polls that were conducted 52 days or less before election day. I decided to have this cutoff be 52 days because in 1952, the closest poll to election day was one that was conducted 51.5 days before.

I also added GDP as a variable because Achen and Bartels (2017) found that it was possible to fairly accurately account for past presidential election outcomes based on how much real income growth voters experienced in the six months leading up to the election. However, also understanding that voters are more likely to remember the last couple months of an official’s term rather than their entire term, I filtered for data from Q7 when examining the GDP growth percentage.

To gather all of these independent variables, I combined the historical data of nationwide vote and seat share from 1948 to 2020 with a dataset of generic ballot results (like I mentioned above, filtering these for polls 52 days before the election) and a data set for GDP data. With the data from the generic ballot, I was sure to make variables for the generic ballot differences. All of these variables were used to predict the seat share of each party, Democrat and Republican, using a simple linear model.


# Model Formulas

I used two formulas for my model, one for each party (note that the train_lm data was the data set after filtering for 2022):

For Democrat seat share: lm(D_seats ~  demballotdif + presparty + D_seats_before + GDP_growth_pct, data = train_lm)
For Republican seat share: lm(R_seats ~  repballotdif + presparty + R_seats_before + GDP_growth_pct, data = train_lm)



```
## # A tibble: 1 × 16
##    year R_votes D_votes R_seats D_seats R_majo…¹ D_maj…² winne…³ D_sea…⁴ R_sea…⁵
##   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>    <dbl>   <dbl> <chr>     <dbl>   <dbl>
## 1  2022      NA      NA      NA      NA       NA      NA <NA>        220     212
## # … with 6 more variables: demballot <dbl>, repballot <dbl>, presparty <chr>,
## #   demballotdif <dbl>, repballotdif <dbl>, GDP_growth_pct <dbl>, and
## #   abbreviated variable names ¹​R_majorvote_pct, ²​D_majorvote_pct,
## #   ³​winner_party, ⁴​D_seats_before, ⁵​R_seats_before
```

```
## 
## Two-Party Seat Share Models
## =======================================================================
##                                           Dependent variable:          
##                                 ---------------------------------------
##                                       D_seats             R_seats      
##                                         (1)                 (2)        
## -----------------------------------------------------------------------
## Dem Generic Ballot Lead/Deficit  1.919*** (0.329)                      
## Rep Generic Ballot Lead/Deficit                      1.845*** (0.328)  
## President's Party               -18.925*** (5.114)   17.606*** (5.004) 
## Dem Seats Before Election        0.379*** (0.090)                      
## Rep Seats Before Election                            0.400*** (0.091)  
## GDP Growth                       -1.681** (0.661)     -0.045 (0.644)   
## Constant                        141.774*** (20.874) 123.458*** (19.423)
## -----------------------------------------------------------------------
## Observations                            36                  36         
## R2                                     0.790               0.787       
## Adjusted R2                            0.763               0.760       
## Residual Std. Error (df = 31)         14.823              14.443       
## F Statistic (df = 4; 31)             29.192***           28.671***     
## =======================================================================
## Note:                                       *p<0.1; **p<0.05; ***p<0.01
```

```
##        fit    lwr      upr
## 1 207.0354 175.67 238.4007
```

```
##        fit      lwr      upr
## 1 223.4344 192.8501 254.0186
```
As shown above, almost all variables, excluding the GDP growth, are statistically significant at the 1% significance level (p < 0.01). For GDP growth used to predict the Democrat seat share, it is statistically significant at the 5% level. The adjusted R squared for Democrats is 0.763 and for Republicans is 0.760. 
As we can see in the generic ballot data, for each additional point lead in the generic ballot, the Democratic party is projected to gain approximately 1.919 seats; for Republicans this projected seat gain is approximately 1.845. This value is similar for both parties. 
Moreover, when looking at the president’s party variable, we can see that if the president is a Democrat, their party will lose about 18 seats, while if the president is a Republican, their party will gain about 17 or 18 seats. Additionally, for every additional seat held before the election, the proportion of a seat that the Democratic party is projected to gain is approximately 0.379; for Republicans that proportion is 0.400. 
GDP growth is a bit more nuanced, given that it lacks the same level of statistical significance as the other variables. According to the data, for every percentage point increase in GDP growth, the Democrats are projected to lose 1.681 seats while the Republicans are projected to lose 0.045 seats. This is not in line with other findings in our reading, and also intuition, and given the relative insignificance of these variables, we can conclude that the GDP growth variable is not very indicative when it comes to predicting a party’s seat share.

# Model Validation

## In-Sample Fit

To conduct an in-sample fit, I use already existing data and examine the r-squareds and compare the in-sample error. In other words, we are looking at how often a prediction on historical data matches the actual historical result. The r-squareds of my model were strong, at about 0.76. To compare the in-sample error, I graphed historical results versus predictions for my models.

<img src="{{< blogdown/postref >}}index_files/figure-html/in-sample-1.png" width="672" />

As seen above, the models for predicting both Democrat and Republican seat share are fairly accurate despite a few points.

## Out-of-Sample Fit

When conducting an out-of-sample fit, we need to withhold one historical observation from the data set to predict its result and examine its accuracy to the actual result. Each of the values below show the result of predicted seat share minus actual seat share for each model. As one can see, for the Democrats, the model predicted a lower value than the actual, and the opposite is true for Republicans.


```
##         1 
## -8.031788
```

```
##        1 
## 6.895323
```

# Prediction Intervals


```
##        Model      Fit      lwr      upr
## 1   Democrat 207.0354 175.6700 238.4007
## 2 Republican 223.4344 192.8501 254.0186
```

<img src="{{< blogdown/postref >}}index_files/figure-html/pred interval-1.png" width="672" />
The two plots above depict the fit, lower, and upper bounds of each model's seat share prediction. For Democrats, the fit is approximately 207 seats, the lower is approximately 175 seats, and the upper is approximately 238 seats. For Republicans, it is approximately 223 seats, 192 seats, and 254 seats, respectively. The dotted line represents 218 seats, which is needed for majority.

# Final Prediction

Given all these findings from my model, my prediction for the 2022 midterm election is that Democrats will win 207 seats and Republicans will win 223 seats in the House of Representatives. This number does not add up to 435 seats because I had two separate models for Democrat seat share and Republican seat share. 
