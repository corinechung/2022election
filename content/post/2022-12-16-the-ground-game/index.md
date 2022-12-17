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
## ===========================================================
##                               Dependent variable:          
##                     ---------------------------------------
##                                     turnout                
##                             (1)                 (2)        
## -----------------------------------------------------------
## avg_rating                -0.003              -0.009       
##                           (0.005)             (0.006)      
##                                                            
## RepStatusIncumbent                             0.032       
##                                               (0.022)      
##                                                            
## Constant                 0.579***            0.587***      
##                           (0.022)             (0.022)      
##                                                            
## -----------------------------------------------------------
## Observations                193                 193        
## R2                         0.002               0.014       
## Adjusted R2               -0.003               0.003       
## Residual Std. Error  0.120 (df = 191)    0.120 (df = 190)  
## F Statistic         0.426 (df = 1; 191) 1.313 (df = 2; 190)
## ===========================================================
## Note:                           *p<0.1; **p<0.05; ***p<0.01
```

The first model shows that there is not a strong relationship between the rating and turnout. However, once incumbency is added, there seems to be a stronger relationship, and the data demonstrates that as a a district is predicted to be more Republican, the turnout decreases by about 0.016 points. Though it has more significance, this is still a small value.
