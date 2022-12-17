---
title: The Ground Game
author: ''
date: ''
slug: []
categories: []
tags: []
---




This week, I examine whether or not there is a relationship between turnout and expert rating. To do so, I run two models: the first seeing if expert rating can predict turnout, and the second doing the same while controlling for incumbency. 


```
## 
## ================================================================
##                                 Dependent variable:             
##                     --------------------------------------------
##                                       turnout                   
##                              (1)                   (2)          
## ----------------------------------------------------------------
## avg_rating                -0.012**              -0.023***       
##                            (0.005)               (0.006)        
##                                                                 
## RepStatusIncumbent                               0.062***       
##                                                  (0.023)        
##                                                                 
## Constant                  0.602***               0.616***       
##                            (0.022)               (0.022)        
##                                                                 
## ----------------------------------------------------------------
## Observations                 193                   193          
## R2                          0.030                 0.065         
## Adjusted R2                 0.025                 0.055         
## Residual Std. Error   0.123 (df = 191)       0.121 (df = 190)   
## F Statistic         5.892** (df = 1; 191) 6.569*** (df = 2; 190)
## ================================================================
## Note:                                *p<0.1; **p<0.05; ***p<0.01
```

The first model shows that there is not a strong relationship between the rating and turnout. However, once incumbency is added, there seems to be a stronger relationship, and the data demonstrates that as a a district is predicted to be more Republican, the turnout decreases by about 0.016 points. Though it has more significance, this is still a small value.
