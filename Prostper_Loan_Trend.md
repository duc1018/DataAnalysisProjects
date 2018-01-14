---
title: "Prosper_Loan_Trend"
author: "Duc"
date: "January 1, 2018"
output:
  html_document:
    keep_md: yes
    toc: yes
    toc_depth: 3
    toc_float: yes
---
#Introduction

The objective of this project is to determine what factors help the loan \
applicants have more investments. By exploring the relationship between the \
number of investors and total trades, we would be able to make  the customers' \
loan applicant more appealing to their investors.

The data set is obtained from the following link:
https://docs.google.com/document/d/1qEcwltBMlRYZT-l699-71TzInWfk4W9q5rTCSvDVMpc/pub?embedded=true
  



# Load Data and neccessary package




Let create a copy of L





#Univariate Plots Section


```
## [1] 113937     81
```


Notes:

The data Set contains 46 variables with 113937 observations.



```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00    2.00   44.00   80.48  115.00 1189.00
```


![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

The histogram seems to be skewed to the right.Also, the mean is much larger \
than the median. This suggests that there is an outlier in this data set. 
\ Perhaps, the number of investors with the value of 1 is the outlier. \
In addition, there are very few values that have large X values. 




Let confirm that the outlier occurs at Investors of the value of 1.

```
##     1 
## 27814
```

Since 1 has the most count, it is an outlier in Investor with the value of 1.\
Except for the outlier, the rest of the distribution seems to be normal.

Let examine this outlier graphically.

![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-6-1.png)<!-- -->




The boxplot shows that we have an outlier. It is necessary to transform the \
Investors variables to near normality.


![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-7-1.png)<!-- -->

Transformed the long tail data to have a better understanding of the \
distribution of Investors. The transformed Investors distribution appears to \
approximately normal. Even though the outlier is still there, we use the median \
mean to analyze the Total trades-Investors trends


```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
##    0.00   15.00   22.00   23.23   30.00  126.00    7544
```

Notice there are still missing values in Total Trades. We will replace them with \
the mean of column TotalTrades.




```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    0.00   15.00   23.00   23.23   29.00  126.00
```

Hence, all the missing values are replaced with the mean of Total Trades. 

![](Prostper_Loan_Trend_files/figure-html/- TotalTrades Plot-1.png)<!-- -->

Because Totaltrade is filled with its mean, approximately 23.23, this value \
has the most count and is associated with the high peak in the plot. The mean \
and median are approximately normal. In addition to the graph, the distribution \
of total trade is approximately normal.




Let examine how the histograms look like accross the categoriacal variable \
of IncomeRange,  IsBorrowerHomeowner, EmploymentStatus.



```
## [1] "$0"             "$1-24,999"      "$100,000+"      "$25,000-49,999"
## [5] "$50,000-74,999" "$75,000-99,999" "Not displayed"  "Not employed"
```

The level of IncomeRange is not in ordered. The "$75,000-99,999" comes after the "100,000+"



To avoid the overlapping x labels, the income re-labeled with the plus signs. \
"+" to indicate the range. For example, 25,000+ show  the range between  \
25,000-49,999

![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-11-1.png)<!-- -->

Most of the income ranges are in 25,000-24,999 and 50,000-74,9999. There are \
very few people with unemployed status and zero income. Now let examine \
Occupation

![](Prostper_Loan_Trend_files/figure-html/- IsBorrowerHomeowner-1.png)<!-- -->


There are as many homeowners as none home owners. So data will be in favor of \
neither group.


![](Prostper_Loan_Trend_files/figure-html/- EmploymentStatus-1.png)<!-- -->


There are some people leave their employment status empty. We will graph the \
plot again without empty employment status.

![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-12-1.png)<!-- -->


```
##                    Employed     Full-time Not available  Not employed 
##          2255         67322         26355          5347           835 
##         Other     Part-time       Retired Self-employed 
##          3806          1088           795          6134
```

Most of the applicants are employed, and there are very few that leaves their \
employment status blank.


# Univariate Analysis
### What is the structure of your dataset?
There are 1113937 listing with 81 variable.The variable EmploymnetStattus, \
IsBorrowerHomeowner,Occupation, are factor variable, except for IncomeRange, \
It is ordered factor variable.

1. Some Observation:
    + The median investors are 44.00 and the max number of investers is 1189
    + There is outlier at Investor of the value 1
    + This outlier is good data in extreme case
    + We will use medians to examine the Totaltrade-Investor trend
    + The missing values in Totaltrade are replaced with its means,23.33
    + The amount of homeoweners and non-homeowner are approximately equal.
    + The majority of applicant are employed.
    + Most of the income ranges are in 25,000-24,999 and 50,000-74,9999
    
### What is/are the main feature(s) of interest in your dataset?
The data set's main feature is Investors and TotalTrades. The objective is to determine \
which factors are best for preditiing the number of Investors for the loans.

### What other features in the dataset do you think will help support your \
investigation into your feature(s) of interest?

The TotalTrades with the combination of other variables, such as Income Range,\
Employment Status, and home owners, can be used to predict a model to Investors numbers.

### Did you create any new variables from existing variables in the dataset?
I have not created any new variable

### Of the features you investigated, were there any unusual distributions? \
Did you perform any operations on the data to tidy, adjust, or change the form \
of the data? If so, why did you do this?

The right-skewed distribution of Investors is log-transformed and square root \
transformed at x, y-axis respectively. The distribution is approximately normal \
except for the outlier at Investors of value 1.


# Bivariate Plots Section

Let examine the correlation between the variable

Create a subset data frame of Loan, that contains the variable of interest




![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-15-1.png)<!-- -->


There is a positive correlation,0.106 between Total trades and Investors, in a small \
sample. Probably, this relationship still hold in large sample




![](Prostper_Loan_Trend_files/figure-html/- explore Investors and TotalTrades Relationship-1.png)<!-- -->


Notes:
The total trades that have the most investors are in the range of 15 to 30. \
The numbers of Investors start decreasing after passing approximately 30 trades.\
Let examine the correlation between TotalTrades and Investors.









```
## cor_Trade_Investors = 0.023
```

```
## 
## Calls:
## m1: lm(formula = Investors ~ TotalTrades, data = Loan)
## 
## =====================================
##   (Intercept)             75.725***  
##                           (0.691)    
##   TotalTrades              0.204***  
##                           (0.027)    
## -------------------------------------
##   R-squared                0.001     
##   adj. R-squared           0.001     
##   sigma                  103.213     
##   F                       58.848     
##   p                        0.000     
##   Log-likelihood     -689970.893     
##   Deviance        1213736621.373     
##   AIC                1379947.786     
##   BIC                1379976.716     
##   N                   113937         
## =====================================
```

In the summary; There is no linear relationship between two variables.\ 
Let examine the total trade and Investors graph again, with the linear regression\
line

![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-17-1.png)<!-- -->

The linear line is nearly horizontally. Along with the correlation coefficience\,
it may indicate that Total trades and Investors do not have the linear relationship.



However, We can still examine how the numbers of Investors vary in \
different numbers of trades.

Let group Investors by numbers of TotalTrade





```
## # A tibble: 4 x 4
##   TotalTrades Mean_Investors Median_Investors     n
##         <dbl>          <dbl>            <dbl> <int>
## 1        0              37.0             34.0     4
## 2        1.00           63.4             46.0   233
## 3        2.00           75.7             55.0   674
## 4        3.00           76.7             52.0   763
```

Let plot the geom_line for the TotalTrades with  Mean_Investors. 

![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-20-1.png)<!-- -->

The average numbers of investors seem to be constant in TotalTrades between 0 and 73. \
Approximately Between the 90 and 126, the Investor Mean decreases. \
Let confirm this pattern with their correlation, in the subset where TotalTrades




```
## cor_Mean_Investors_at_least_Than_94 Trade = -0.266
```

```
## cor_Mean_Investors_lessThan_94 Trade = -0.01
```


Perhaps, TotalTrades of at least 94 correlates with numbers of Investors. \
We shall fit a linear regression model on the variables


```
## 
## Calls:
## m2: lm(formula = Mean_Investors ~ TotalTrades, data = subset(L.invest_by_trade, 
##     TotalTrades >= 94))
## 
## ===============================
##   (Intercept)        511.906   
##                     (389.970)  
##   TotalTrades         -3.650   
##                       (3.668)  
## -------------------------------
##   R-squared            0.071   
##   adj. R-squared      -0.001   
##   sigma              137.633   
##   F                    0.990   
##   p                    0.338   
##   Log-likelihood     -94.080   
##   Deviance        246255.224   
##   AIC                194.159   
##   BIC                196.283   
##   N                   15       
## ===============================
```

The correlation -0.266 suggests that is the negative correlation between Mean_Investor, \
and TotalTrades of at least 94. The R-squared implies that is 7.1 % in variance \
in Mean Investors. Perhaps, TotalTrades and Investors correlates negatively with \
each others , when total trades is are at least 94.


```
## cor_Investors_at_least_Than_94 Trade = -0.299
```

```
## cor_Investors_lessThan_94 Trade = 0.022
```

The correlation -0.266 suggests that is the negative correlation between Mean_Investor, \
and TotalTrades of at least 94. The R-squared implies that is 7.1 % in variance \
in Mean Investors. Perhaps, TotalTrades and Investors correlates negatively with \
each other, when total trades are are at least 94.



Let examine how categorical features vary with Total Trades and Investors

![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-23-1.png)<!-- -->

Notice there are some  Outliers in each category. Take a closer look at medians \
of each category

![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-24-1.png)<!-- -->

Full-time Status has the highest median and average(x symbol), while other and \
employed have the lowest medians.

A Summary relationship between Investors and Employment Status


```
## Non_NA_Status$EmploymentStatus: 
## NULL
## -------------------------------------------------------- 
## Non_NA_Status$EmploymentStatus: Employed
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00    1.00   24.00   64.55   91.00  779.00 
## -------------------------------------------------------- 
## Non_NA_Status$EmploymentStatus: Full-time
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##     1.0    44.0    93.0   130.2   177.0  1189.0 
## -------------------------------------------------------- 
## Non_NA_Status$EmploymentStatus: Not available
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00   23.00   47.00   76.14   99.00  740.00 
## -------------------------------------------------------- 
## Non_NA_Status$EmploymentStatus: Not employed
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00   19.00   42.00   60.34   76.00  432.00 
## -------------------------------------------------------- 
## Non_NA_Status$EmploymentStatus: Other
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00    1.00   21.00   47.33   66.00  640.00 
## -------------------------------------------------------- 
## Non_NA_Status$EmploymentStatus: Part-time
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00   34.00   65.50   86.25  119.00  522.00 
## -------------------------------------------------------- 
## Non_NA_Status$EmploymentStatus: Retired
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00   35.00   68.00   91.92  124.00  586.00 
## -------------------------------------------------------- 
## Non_NA_Status$EmploymentStatus: Self-employed
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00    1.00   44.00   78.79  117.00  912.00
```

Not just median, full-time status has the largest average numbers of Investors. \
Perhaps, Investors are more confident with the full-time applicants, because they \
have the stable income. The other and employed status approximately have equal \
median. Probably the status "other" and "employed" are vague. As a result, the \
investors find it difficult to make the investment with them.


Next, we'll look how homeowning status affects the number of investors.

![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-26-1.png)<!-- -->

```
## Loan$IsBorrowerHomeowner: False
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00    3.00   39.00   67.44   95.00  917.00 
## -------------------------------------------------------- 
## Loan$IsBorrowerHomeowner: True
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00    1.00   50.00   93.27  139.00 1189.00
```

Both the box plot and summary suggest that homeowners are more appealing to \
investors. They have more investors on average and median than non-owner do. \
Probably, their properties increase their credibility.



Now, let exam the income range and Investors

![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-28-1.png)<!-- -->


```
## Loan$IncomeRange: $0
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##     1.0    32.0    76.0   112.1   153.0   558.0 
## -------------------------------------------------------- 
## Loan$IncomeRange: $1-24,999
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00   14.00   43.00   58.54   81.00  518.00 
## -------------------------------------------------------- 
## Loan$IncomeRange: $25,000-49,999
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00    4.00   44.00   68.93  100.00  917.00 
## -------------------------------------------------------- 
## Loan$IncomeRange: $50,000-74,999
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##     1.0     1.0    43.0    79.4   119.0  1024.0 
## -------------------------------------------------------- 
## Loan$IncomeRange: $75,000-99,999
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00    1.00   44.00   88.97  137.00 1189.00 
## -------------------------------------------------------- 
## Loan$IncomeRange: $100,000+
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##       1       1      50     110     173    1035 
## -------------------------------------------------------- 
## Loan$IncomeRange: Not displayed
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00   21.00   41.00   68.42   88.00  740.00 
## -------------------------------------------------------- 
## Loan$IncomeRange: Not employed
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00   19.00   42.00   59.64   76.00  432.00
```

The trend of this relation ship is quite strange. The applicants with zero \
income have more investors on average than the rest of group.
                                                                                                                   



# Bivariate Analysis


### Talk about some of the relationships you observed in this part of the \
investigation. How did the feature(s) of interest vary with other features in \
the dataset?

Both the graph and the correlation suggests no relationship between total \
trades and investors.  Then the relationship is investigated again with the \
the average number of investors.

As the number of trade increases, there is no variance in the number of \
investors. The correlation of at most 94 trade and Investors are approximate \
zero. However, the correlation between the number of investors of at least 94 \
and Investor is around negative 0.3. The number suggests a negative \
correlation between the two variables.

Having the good employment status, such as full time, and property somehow \
associates with the high number of investors. On the contrary, having zero \
income have the most investors on average. This could be some practical \
significance. Probably the applicants have brilliant business ideas.

# Multivariate Plots Section






```
## # A tibble: 6 x 5
##   TotalTrades IsBorrowerHomeowner mean_Investors_count median_Inves~     n
##         <dbl> <fctr>                             <dbl>         <dbl> <int>
## 1        0    False                               37.0          34.0     4
## 2        1.00 False                               62.8          46.0   229
## 3        1.00 True                                95.2         100       4
## 4        2.00 False                               75.5          55.0   657
## 5        2.00 True                                85.9          67.0    17
## 6        3.00 False                               74.9          51.0   717
```


Let examine how the homeowner capture the substantial differences in numbers of investor

![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-31-1.png)<!-- -->

The graph suggests that homeowners have the more total trades than their \
counterparts. Also, the property owners have more investors than the ones who do not.\
The above graph also indicates a property difference is largest for the applicant with at \
least 90 trades. Let further explore how the homeowner status affects the relationship between TotalTrades and Investor


The variable true and false have been repeated for each trade. \
This new data frame will have one row for each trade, and then we put the \
median investor count in True and False.


```
##   TotalTrades False  True
## 1           0    34    NA
## 2           1    46 100.0
## 3           2    55  67.0
## 4           3    51  61.5
## 5           4    50  49.0
```



```
## TotalTrades       False        True 
##           0          23           2
```

There are some total trades with don't have median_investors_count, \
because they belong exclusively to the homeowner or non-homeowner group. \
We will plot the ratio of the nonhomeowner to homeowner median_inestor_count

![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-34-1.png)<!-- -->

In the Homeowner to Nonhomeowner, total trade of at least 80, the homeowners \
have twenty times as the non-home owners. \
The non-homeowner to homeowner shows that non- homeowner has over five-time as \
the homeowners, when their total trades range is between 70 and 80 trades. \
In both graphs, the ratio of the trades below 80, almost matches the intercept. \
This could mean that is no significance when the total trades are in that range.



```
## cor_Investors_Yes_home= 0.26
```

```
## cor_Investors_No_home = -0.258
```


Surprisingly! there is the pattern in Investors and TotalTrades Relationship \
when taking account of the homeowners. The TotalTrades have the positive correlation \
with the Investors, if the applicants are the home owner. In contrast, it \
is a negative correlation when applicants are the non-homeowner.


```
## [1] 19 81
```

There are only 19 observations to show the negative correlation between \
Investors and TotalTrades.There are very few TotalTrades with high values. \
Adding Home owners status somehow solve that issue.\
we will see how the Investor-TotalTrade improve with the third variable



Next we shall explore how the employment status effect Investors and \
TotalTrades's relationship

First Create a - Create a dataframe, that group TotalTrades with EmploymentStatus


```
## # A tibble: 3 x 5
##   TotalTrades EmploymentStatus mean_Investors_count median_Investor~     n
##         <dbl> <fctr>                          <dbl>            <dbl> <int>
## 1        0    Full-time                        54.0             54.0     2
## 2        0    Not available                    20.0             20.0     2
## 3        1.00 Employed                         55.5             48.0    59
```



![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-39-1.png)<!-- -->

The retired, Full-time, and self-employed seem to have strong correlation \
with median_Investors_count.Let calculate to confirm their correlation


Frist transform it to then we put the median investor count in employment status


```
##   TotalTrades Employed Full-time Not available Not employed Other
## 1           0       NA      54.0            20           NA    NA
## 2           1     48.0      44.0            NA         31.5  59.0
## 3           2     41.0      76.0            NA         52.0  44.5
## 4           3     39.5      73.5            23         34.5  32.0
## 5           4     39.0      62.0           118         44.5  31.0
##   Part-time Retired Self-employed
## 1        NA      NA            NA
## 2      52.5    33.0            46
## 3      66.0   146.0            43
## 4      51.0    44.5            70
## 5      50.0    64.0            52
```

There are some missing values, let replace them with the columns mean








Check if there are any missing value

```
## [1] FALSE
```

Calculate the correlation



```
## cor_ Employed _TotalTrade =   0.288 
## cor_ Full-time _TotalTrade =   0.214 
## cor_ Not available _TotalTrade =   0.034 
## cor_ Not employed _TotalTrade =   0.011 
## cor_ Other _TotalTrade =   -0.08 
## cor_ Part-time _TotalTrade =   0.121 
## cor_ Retired _TotalTrade =   0.156 
## cor_ Self-employed _TotalTrade =   0.147
```

It turns out that total trades in Employed and Full_Time status have the \
highest correlation, compared to the remaining group.


Now let examine the income ranges


![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-44-1.png)<!-- -->


The zero income may be positively correlated with the number of investors, \
as the red line looks increasing. The other lines, associated with other\
income ranges, seem to be decreasing. \
Let confirm this observation with correlation coefficient and graphs




![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-46-1.png)<!-- -->


The investors, with zero income and one hundred grand income group, seem to \
increase as the trades increase

Let calculate the correlation.


```
##   TotalTrades   $0 $1-24,999 $25,000-49,999 $50,000-74,999 $75,000-99,999
## 1           0   NA        NA           54.0             NA             NA
## 2           1 26.5        46           51.5           40.0           56.0
## 3           2 43.5        50           58.0           87.0           58.5
## 4           3 31.0        44           67.0           66.5           53.0
## 5           4 36.0        48           50.0           57.0           91.0
##   $100,000+ Not displayed Not employed
## 1        NA          20.0           NA
## 2        19          52.0         32.0
## 3        53          17.5         50.5
## 4        68          23.0         35.5
## 5        64          87.5         48.0
```



```
## cor_ $0 _TotalTrade =   0.328 
## cor_ $1-24,999 _TotalTrade =   0.043 
## cor_ $25,000-49,999 _TotalTrade =   -0.084 
## cor_ $50,000-74,999 _TotalTrade =   0.251 
## cor_ $75,000-99,999 _TotalTrade =   0.01 
## cor_ $100,000+ _TotalTrade =   0.341 
## cor_ Not displayed _TotalTrade =   0.287 
## cor_ Not employed _TotalTrade =   0.043
```

The total trades of the income of at least 100,000  have positive \
correlation 0.341. It is as close a zero income. 


Let try to fit a Linear Model to this TotalTrades and Investors relationships \
with all the variables, Income range, Employment Status and home owner status \
because there is no correlation for total trades at most 94. We have to fit the \
linear model for the at least 94 trades.


```
## 
## Calls:
## m1: lm(formula = Investors ~ TotalTrades, data = atleast_94_trades)
## m2: lm(formula = Investors ~ TotalTrades + IsBorrowerHomeowner, data = atleast_94_trades)
## m3: lm(formula = Investors ~ TotalTrades + IsBorrowerHomeowner + 
##     EmploymentStatus, data = atleast_94_trades)
## m4: lm(formula = Investors ~ TotalTrades + IsBorrowerHomeowner + 
##     EmploymentStatus + IncomeRange, data = atleast_94_trades)
## 
## ================================================================================================
##                                                 m1           m2           m3           m4       
## ------------------------------------------------------------------------------------------------
##   (Intercept)                                  640.205      486.813      534.705      308.084   
##                                               (385.639)    (439.249)    (401.135)    (429.315)  
##   TotalTrades                                   -4.749       -4.344       -5.936       -3.270   
##                                                 (3.675)      (3.759)      (3.449)      (3.896)  
##   IsBorrowerHomeowner: True/False                           117.236      186.779      124.874   
##                                                            (153.750)    (141.683)    (147.428)  
##   EmploymentStatus: Full-time/Employed                                   127.271      140.105   
##                                                                          (64.853)     (65.358)  
##   EmploymentStatus: Self-employed/Employed                              -144.678      -35.280   
##                                                                         (141.942)    (160.231)  
##   IncomeRange: .L                                                                      -3.568   
##                                                                                       (72.659)  
##   IncomeRange: .Q                                                                      97.347   
##                                                                                       (71.963)  
## ------------------------------------------------------------------------------------------------
##   R-squared                                      0.089        0.121        0.382        0.474   
##   adj. R-squared                                 0.036        0.012        0.205        0.212   
##   sigma                                        146.313      148.148      132.820      132.304   
##   F                                              1.669        1.105        2.164        1.805   
##   p                                              0.214        0.355        0.126        0.181   
##   Log-likelihood                              -120.632     -120.293     -116.950     -115.411   
##   Deviance                                  363926.649   351165.584   246976.841   210051.178   
##   AIC                                          247.265      248.587      245.899      246.822   
##   BIC                                          250.098      252.364      251.566      254.378   
##   N                                             19           19           19           19       
## ================================================================================================
```
The variable in this linear model can accounts for 47.4% of variance in the \
number of investors.


# Multivariate Analysis

investigation. Were there features that strengthened each other in terms of \
looking at your feature(s) of interest?

The homeowner status reflects the relationship between Investors and Total trades \
. There are very few data for high total trades values. As result, \
the correlation between Investor and Total trades is zeros. After dividing the \
total trade in two parts, we find that total trade with value at least 94 \
is negatively correlated with the Investors. 

By including homeowner status, the Investor-Total trades trend is noticeable. \
For homeowner, it is positively correlated with the value of 0.26, \
and -0.258 for the negative correlation. We can see the trend as whole without \
dividing the total trades. 

In this case the, total trades with nonhomeowner status increase as \
the Investor decrease. The opposite effect is produced by total trades homeowner \
status.

### Were there any interesting or surprising interactions between features?

We also apply the similar approach. We explore the Investor-Total trades trend \
, with Employment status. There is a positive correlation between them, in the \
the term of employment status. For example, the total trade in the employed status \
has the correlation 0.288.


In the same manner, the income range variable also illustrates the similar. \
The income of at least 100,000 graphs and its correlation 0.341 suggests that \
the investors increase as the total trade increase. However, total trades \
with zeros, income seems to be strange, when it has the positive correlation.


### OPTIONAL: Did you create any models with your dataset? Discuss the \
strengths and limitations of your model.\
The linear models with the R square 0.474, demonstrates how we can use the \
variables to predict the Investor-Total trades trend. 

# Final Plots and Summary
### Plot One


![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-50-1.png)<!-- -->

### Description One

Using number of investors as the resposne variable is problematic, beause \
there is an outlier at investors of value of 1. In addition, there are very \
few values of total trades with hight values. We transform the data to make it \
look as normally distributed as possible.

### Plot Two
![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-51-1.png)<!-- -->


### Description Two
Investor vs TotalTrades is produced from the data set. It does not seems to \
resemble any pattern.  Next, the Average Investor and Total Trades graph does \
show a lot of flunction in Mean investors. However both graph show the \
decreasing pattern around the total trades of 94. The linear regression line in \
each graph may suggest that two variables don not hold any linear relationship \
because the lines seems to be horizontal.


### Plot Three
![](Prostper_Loan_Trend_files/figure-html/unnamed-chunk-52-1.png)<!-- -->

### Description Three

Adding one of the three variables makes the Investor - TotalTrade trend \
noticeable. The total trades in the homeowning group increases as the investors \ 
increases. 

As the confidence curves, the ellipse shows that the majority of \
homeowners and nonhomeowner are concentrated the total trade range \  
between zero and fifty. 

The two ellipses are not circular. This means that the TotalTrades and Investor \
are correlated, in term of homeowning status.

The slope of non-homeowner is slightly negative; this suggests that the  Total \
Trade is negatively correlated with the numbers of Investors. The regression line\
also illustrates that pattern.

The slope of homeowner group is approximately constant. However the linear regression\
line 's slope is slightly positive, for the homeowners with more trades. This can be \
caused by the data collecting process. There are very few applicants with more \
investors in the data set.

# Reflection

The objective of this project is using Investors as the response variable to measure how appealing \
is the listing. The total trades variable is used as the predict the number of investors. 

In the beginning, they do not correlate. The correlation coefficient is as low as zero. After splitting \
the total trades at 94. We find that Investor-Total trend is negatively correlated,-0.299, Perhaps we \
can use this subset to explore. However, there are only 19 observation, for the total trades of at \
least 94.

To solve this issue, we explore the Investor-total trade relationship in term of three variables, \
income-range, employment, and homeowning status. Surprisingly, they display the increasing patterns.\
Except for non-homeowner status, the trend is decreasing, with correlation coefficient -0.258.

Perhaps, there are some problems with the data collections. It should be a better way to collect the data.



#Acknowledgement

Thank you Udacity project reviewers, my mentors, and staff. Below are the links I used to complete this project.

https://stackoverflow.com/questions/25835643/replace-missing-values-with-column-mean

http://www.okstate.edu/sas/v8/sashtml/insight/chap18/sect3.htm


