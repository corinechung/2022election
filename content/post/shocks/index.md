---
title: Shocks
author: ''
date: ''
slug: []
categories: []
tags: []
---

# Shocks

As discussed in class and section, election shocks are events that couldn't have been predicted but could significantly affect election outcomes. Examples of shocks from this year include the overturning of Roe v. Wade via the Dobbs decision and the war in Ukraine. Though it is difficult to truly measure the impact of a given shock, we can turn to polls to see how a shock can affect public opinion.

# Model

I will not be using a pooled model for my final prediction because I will be examining the United States as a whole instead of focusing on a district-level approach. I am taking a nation-wide approach because redistricting (and the addition of new districts) makes a district-level approach difficult and perhaps even unreliable.

For my model, I will be starting with GDP as one predictive variable, since economic growth or decline is something felt by and recognized by all US inhabitants. 








```
## # A tibble: 0 × 9
## # … with 9 variables: year <dbl>, R_votes <dbl>, D_votes <dbl>, R_seats <dbl>,
## #   D_seats <dbl>, R_majorvote_pct <dbl>, D_majorvote_pct <dbl>,
## #   winner_party <chr>, GDP_growth_pct <dbl>
```

```
## 
## Two-Party Seat Share Models
## ===================================================================
##                                        Dependent variable:         
##                               -------------------------------------
##                                    D_seats            R_seats      
##                                      (1)                (2)        
## -------------------------------------------------------------------
## GDP Growth                      -1.472 (1.335)     -0.220 (1.329)  
## Constant                      239.518*** (5.253) 192.697*** (5.228)
## -------------------------------------------------------------------
## Observations                          37                 37        
## R2                                  0.034              0.001       
## Adjusted R2                         0.006              -0.028      
## Residual Std. Error (df = 35)       30.085             29.942      
## F Statistic (df = 1; 35)            1.216              0.027       
## ===================================================================
## Note:                                   *p<0.1; **p<0.05; ***p<0.01
```

It is obvious that this model is not ideal, since it only has one variable to predict seatshare. Moreover, according to the data, for every percentage point increase in GDP growth, the Democrats are projected to lose 1.472 seats while the Republicans are projected to lose 0.220 seats. This is not in line with other findings in our reading, and also intuition, and given the relative insignificance of these variables, we can conclude that the GDP growth variable is not very indicative when it comes to predicting a party’s seat share. However, I am curious to see if this will change with the addition of other variables into the model.
