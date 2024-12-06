# Final Examination

## Due Friday, December 6, 2024 at 11:59 PM in your GitHub repository.

Complete the exercise described in the pdf above and enter your answers in 
the spaces below.

*Please see the revised version of the pdf copy of the question paper, uploaded Nov. 23, 2024.*

## Part A: Data Handling and Preliminary Regression Modelling

### Question 1

a) Read in the ```airplane_sales.csv``` dataset and store it in a data frame called ```airplane_sales``` in your workspace. 


```

> airplane_sales <- read.csv('airplane_sales.csv')

```

b) Calculate and copy the printed output from a ```summary``` of the data. 
Use this to get familiar with the contents of the dataset. 


```
summary(airplane_sales)
   X0Sale_ID          age            price       
 Min.   :101.0   Min.   :13.00   Min.   :  9000  
 1st Qu.:149.5   1st Qu.:19.00   1st Qu.: 19250  
 Median :198.0   Median :22.00   Median : 33500  
 Mean   :198.0   Mean   :24.61   Mean   : 50237  
 3rd Qu.:246.5   3rd Qu.:30.00   3rd Qu.: 73500  
 Max.   :295.0   Max.   :44.00   Max.   :254000 

```

c) Estimate a regression model to predict ```price``` as a function of ```age```. 
Copy the printed estimation output from the ```summary``` command. 


```
summary(lm_model_1)

Call:
lm(formula = price ~ age, data = airplane_sales)

Residuals:
   Min     1Q Median     3Q    Max 
-58685 -19747  -6039  15903 170846 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) 144322.9     8426.0   17.13   <2e-16 ***
age          -3823.0      329.5  -11.60   <2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 31910 on 193 degrees of freedom
Multiple R-squared:  0.4108,	Adjusted R-squared:  0.4078 
F-statistic: 134.6 on 1 and 193 DF,  p-value: < 2.2e-16

```


### Question 2

a) Read in the ```airplane_specs.csv``` dataset and store it 
in a data frame called ```airplane_specs``` in your workspace. 


```
airplane_specs <- read.csv('airplane_specs.csv')

```

b)  Form a dataset ```airplane_sales_specs.csv``` 
by ```merge```ing the data frames 
```airplane_sales.csv``` and ```airplane_specs.csv```. 
Store the new dataset in a data frame called 
```airplane_sales_specs``` in your workspace. 


```
airplane_sales_specs <- merge(airplane_sales, airplane_specs)

```


c) Calculate and copy the printed output from a ```summary``` of the data. 
Use this to get familiar with the contents of the dataset. 


```

summary(airplane_sales_specs)
   X0Sale_ID          age            price             pass            wtop       
 Min.   :101.0   Min.   :13.00   Min.   :  9000   Min.   :2.000   Min.   :0.0000  
 1st Qu.:149.5   1st Qu.:19.00   1st Qu.: 19250   1st Qu.:4.000   1st Qu.:0.0000  
 Median :198.0   Median :22.00   Median : 33500   Median :4.000   Median :0.0000  
 Mean   :198.0   Mean   :24.61   Mean   : 50237   Mean   :4.287   Mean   :0.4615  
 3rd Qu.:246.5   3rd Qu.:30.00   3rd Qu.: 73500   3rd Qu.:6.000   3rd Qu.:1.0000  
 Max.   :295.0   Max.   :44.00   Max.   :254000   Max.   :6.000   Max.   :1.0000  
    fixgear           tdrag        
 Min.   :0.0000   Min.   :0.00000  
 1st Qu.:0.0000   1st Qu.:0.00000  
 Median :0.0000   Median :0.00000  
 Mean   :0.4513   Mean   :0.05641  
 3rd Qu.:1.0000   3rd Qu.:0.00000  
 Max.   :1.0000   Max.   :1.00000  

```


d) Estimate a regression model to predict ```price``` as a function of 
```age```, ```pass```, ```wtop```, ```fixgear```, 
and ```tdrag```. 
Copy the printed estimation output from the ```summary``` command. 


```

 lm_model_2 <- lm(data = airplane_sales_specs,
+                          formula = price ~ age + pass + wtop + fixgear)
> summary(lm_model_2)

Call:
lm(formula = price ~ age + pass + wtop + fixgear, data = airplane_sales_specs)

Residuals:
   Min     1Q Median     3Q    Max 
-31489 -14036  -4367  10283 147149 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  51987.3     9057.7   5.740 3.70e-08 ***
age          -2603.5      261.7  -9.949  < 2e-16 ***
pass         12819.4     1481.6   8.652 2.11e-15 ***
wtop         -3215.7     3515.4  -0.915    0.361    
fixgear      19602.8     4517.2   4.340 2.32e-05 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 22570 on 190 degrees of freedom
Multiple R-squared:  0.7098,	Adjusted R-squared:  0.7037 
F-statistic: 116.2 on 4 and 190 DF,  p-value: < 2.2e-16

```




### Question 3

a) Read in the ```airplane_perf.csv``` dataset and store it 
in a data frame called ```airplane_perf``` in your workspace. 


```

airplane_perf <- read.csv('airplane_perf.csv')

```

b) Form a dataset ```airplane_full.csv``` 
by ```merge```ing all three datasets. 
Store the new dataset 
in a data frame called ```airplane_full``` in your workspace. 


```
airplane_full <- merge(airplane_sales_specs,airplane_perf)

```

c) Calculate and copy the printed output from a ```summary``` 
of the new variables. 
Use this to get familiar with the contents of the dataset. 


```

summary(airplane_full)
   X0Sale_ID          age            price             pass            wtop       
 Min.   :101.0   Min.   :13.00   Min.   :  9000   Min.   :2.000   Min.   :0.0000  
 1st Qu.:149.5   1st Qu.:19.00   1st Qu.: 19250   1st Qu.:4.000   1st Qu.:0.0000  
 Median :198.0   Median :22.00   Median : 33500   Median :4.000   Median :0.0000  
 Mean   :198.0   Mean   :24.61   Mean   : 50237   Mean   :4.287   Mean   :0.4615  
 3rd Qu.:246.5   3rd Qu.:30.00   3rd Qu.: 73500   3rd Qu.:6.000   3rd Qu.:1.0000  
 Max.   :295.0   Max.   :44.00   Max.   :254000   Max.   :6.000   Max.   :1.0000  
    fixgear           tdrag             horse            fuel       
 Min.   :0.0000   Min.   :0.00000   Min.   :108.0   Min.   : 29.00  
 1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:180.0   1st Qu.: 51.00  
 Median :0.0000   Median :0.00000   Median :210.0   Median : 68.00  
 Mean   :0.4513   Mean   :0.05641   Mean   :219.2   Mean   : 67.79  
 3rd Qu.:1.0000   3rd Qu.:0.00000   3rd Qu.:285.0   3rd Qu.: 84.00  
 Max.   :1.0000   Max.   :1.00000   Max.   :310.0   Max.   :130.00  
    ceiling          cruise     
 Min.   : 8500   Min.   : 97.0  
 1st Qu.: 9700   1st Qu.:119.0  
 Median :13000   Median :144.0  
 Mean   :14007   Mean   :144.7  
 3rd Qu.:16800   3rd Qu.:170.0  
 Max.   :28000   Max.   :221.0 

```


d) Estimate a regression model to predict ```price``` as a function of 
```age```, ```pass```, ```wtop```, ```fixgear```, 
and ```tdrag```, 
as well as ```horse```, ```fuel```, ```ceiling```, and ```cruise```.
Copy the printed estimation output from the ```summary``` command. 


```
summary(lm_model_4)

Call:
lm(formula = price ~ age + pass + wtop + fixgear + tdrag + horse + 
    fuel + ceiling + cruise, data = airplane_full)

Residuals:
   Min     1Q Median     3Q    Max 
-40971  -9653  -1189   7035 127745 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept) -4.189e+04  1.440e+04  -2.910  0.00406 ** 
age         -2.354e+03  2.338e+02 -10.070  < 2e-16 ***
pass         5.586e+03  2.218e+03   2.518  0.01264 *  
wtop        -9.928e+03  3.118e+03  -3.184  0.00170 ** 
fixgear     -3.096e+04  6.802e+03  -4.552 9.62e-06 ***
tdrag       -4.925e+04  7.909e+03  -6.226 3.13e-09 ***
horse        2.241e+02  6.720e+01   3.335  0.00103 ** 
fuel        -3.038e+01  1.264e+02  -0.240  0.81033    
ceiling      1.525e+00  5.261e-01   2.899  0.00420 ** 
cruise       5.460e+02  1.117e+02   4.886 2.22e-06 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 18840 on 185 degrees of freedom
Multiple R-squared:  0.8032,	Adjusted R-squared:  0.7936 
F-statistic:  83.9 on 9 and 185 DF,  p-value: < 2.2e-16

```






## Part B: Advanced Regression Modelling


### Question 4

a) Create new variables 
	```log_price```, ```log_age```, ```log_horse```, 
	```log_fuel```, ```log_ceiling```, and ```log_cruise```
	from the variables 
	```price```, ```age```, ```horse```, 
	```fuel```, ```ceiling```, and ```cruise```, 
	using the logarithm function ```log()``` in ```R``` 
	to create these new variables. 


```

airplane_full[, 'log_price'] <- log(airplane_full[, 'price'])
airplane_full[, 'log_age'] <- log(airplane_full[, 'age'])
airplane_full[, 'log_horse'] <- log(airplane_full[, 'horse'])
airplane_full[, 'log_fuel'] <- log(airplane_full[, 'fuel'])
airplane_full[, 'log_ceiling'] <- log(airplane_full[, 'ceiling'])
airplane_full[, 'log_cruise'] <- log(airplane_full[, 'cruise'])

```

b) Calculate and copy the printed output from a ```summary``` 
of the new variables. 
Use this to get familiar with the contents of the dataset. 


```
> summary (airplane_full[, 'log_price'])
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  9.105   9.865  10.419  10.519  11.205  12.445 
> summary (airplane_full[, 'log_age'])
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  2.565   2.944   3.091   3.166   3.401   3.784 
> summary (airplane_full[, 'log_horse'])
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  4.682   5.193   5.347   5.349   5.652   5.737 
> summary (airplane_full[, 'log_fuel'])
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  3.367   3.932   4.220   4.169   4.431   4.868 
> summary (airplane_full[, 'log_ceiling'])
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  9.048   9.180   9.473   9.499   9.729  10.240 
> summary (airplane_full[, 'log_cruise'])
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  4.575   4.779   4.970   4.953   5.136   5.398 

```


c) Estimate a regression model to predict ```log_price``` as a function of 
	```log_age```, ```pass```, ```wtop```, ```fixgear```, 
	and ```tdrag```, 
	as well as 
	```log_horse```, ```log_fuel```, ```log_ceiling```, 
	and ```log_cruise```. 
	Copy the printed estimation output from the ```summary``` command. 


```
lm_model_5 <- lm(data = airplane_full,
formula = log_price ~ log_age + pass + wtop + fixgear + tdrag + log_horse + log_fuel + log_ceiling + log_cruise )
 
summary(lm_model_5)

Call:
lm(formula = log_price ~ log_age + pass + wtop + fixgear + tdrag + 
    log_horse + log_fuel + log_ceiling + log_cruise, data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.50754 -0.11123  0.00186  0.11226  0.53375 

Coefficients:
             Estimate Std. Error t value Pr(>|t|)    
(Intercept)  3.786112   1.067378   3.547 0.000494 ***
log_age     -1.527922   0.063521 -24.054  < 2e-16 ***
pass         0.048006   0.021645   2.218 0.027776 *  
wtop        -0.048649   0.031384  -1.550 0.122823    
fixgear     -0.179043   0.075662  -2.366 0.018998 *  
tdrag       -0.459069   0.081906  -5.605 7.47e-08 ***
log_horse    1.021321   0.135777   7.522 2.27e-12 ***
log_fuel     0.167589   0.084245   1.989 0.048141 *  
log_ceiling -0.005037   0.088651  -0.057 0.954748    
log_cruise   1.086126   0.195242   5.563 9.18e-08 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1896 on 185 degrees of freedom
Multiple R-squared:  0.9438,	Adjusted R-squared:  0.9411 
F-statistic: 345.5 on 9 and 185 DF,  p-value: < 2.2e-16

```


d) If you notice that any coefficients are statistically insignificant, 
	estimate the model by removing them one at a time. 
	For each variable removed, 
	determine whether the variable should be removed 
	by considering the four specification criteria: 
		statistically significant $t$-statistics, 
		an increase in ```R-bar-squared```, 
		a good theoretical justification, and 
		no large change in the other coefficients.


```
lm_model_6 <- lm(data = airplane_full,
+     formula = log_price ~ log_age + pass + fixgear + tdrag + log_horse + log_fuel + log_ceiling + log_cruise )
> 
> summary(lm_model_6)

Call:
lm(formula = log_price ~ log_age + pass + fixgear + tdrag + log_horse + 
    log_fuel + log_ceiling + log_cruise, data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.49050 -0.11120  0.01233  0.11318  0.55682 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  4.24337    1.02967   4.121 5.67e-05 ***
log_age     -1.52909    0.06376 -23.984  < 2e-16 ***
pass         0.05215    0.02156   2.419   0.0165 *  
fixgear     -0.13729    0.07097  -1.934   0.0546 .  
tdrag       -0.45681    0.08220  -5.557 9.39e-08 ***
log_horse    0.98983    0.13475   7.345 6.24e-12 ***
log_fuel     0.17135    0.08453   2.027   0.0441 *  
log_ceiling -0.02693    0.08785  -0.307   0.7595    
log_cruise   1.05544    0.19497   5.413 1.89e-07 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1903 on 186 degrees of freedom
Multiple R-squared:  0.9431,	Adjusted R-squared:  0.9407 
F-statistic: 385.5 on 8 and 186 DF,  p-value: < 2.2e-16

The wtop variable is statistically insignificant and should be removed from the regression model. 
The adjusted R-squared value decreased slightly after its removal, indicating that it doesn't contribute significantly to the model. 
While the choice of wing position (low wings vs. top wings) might influence performance and safety in aircraft design, it is not the primary factor considered when evaluating airplane prices. 
No significant changes were observed in the other coefficients after its removal.

```

Next regression model:

```
lm_model_7 <- lm(data = airplane_full,
+     formula = log_price ~ log_age + pass + fixgear + tdrag + log_horse + log_fuel + log_cruise )
> summary(lm_model_7)

Call:
lm(formula = log_price ~ log_age + pass + fixgear + tdrag + log_horse + 
    log_fuel + log_cruise, data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.49050 -0.10900  0.01349  0.11515  0.54790 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  4.07670    0.87236   4.673 5.66e-06 ***
log_age     -1.52942    0.06359 -24.051  < 2e-16 ***
pass         0.05188    0.02149   2.414   0.0167 *  
fixgear     -0.14417    0.06717  -2.147   0.0331 *  
tdrag       -0.46649    0.07571  -6.161 4.32e-09 ***
log_horse    0.98598    0.13384   7.367 5.44e-12 ***
log_fuel     0.17238    0.08426   2.046   0.0422 *  
log_cruise   1.04191    0.18944   5.500 1.24e-07 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1898 on 187 degrees of freedom
Multiple R-squared:  0.9431,	Adjusted R-squared:  0.941 
F-statistic: 442.7 on 7 and 187 DF,  p-value: < 2.2e-16

The log_ceiling variable is statistically insignificant and should be removed from the regression model.
The adjusted R-squared value increased slightly when it was excluded, suggesting that it doesn't add significant value to the model. 
While the maximum flying altitude of an airplane is important, it typically depends on the specific type of aircraft.
Commercial airplanes are the primary concern when it comes to high altitudes, so this variable may not be as critical for the current context. 
No significant changes were observed in the other coefficients after its removal.

```

Next regression model, if necessary:

```
lm_model_8 <- lm(data = airplane_full,
+     formula = log_price ~ log_age + fixgear + tdrag + log_horse + log_fuel + log_cruise )
> summary(lm_model_8)

Call:
lm(formula = log_price ~ log_age + fixgear + tdrag + log_horse + 
    log_fuel + log_cruise, data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.46666 -0.11163 -0.01509  0.11560  0.56091 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  3.49038    0.84856   4.113 5.83e-05 ***
log_age     -1.56393    0.06276 -24.921  < 2e-16 ***
fixgear     -0.13197    0.06783  -1.946   0.0532 .  
tdrag       -0.42275    0.07445  -5.678 5.09e-08 ***
log_horse    1.18481    0.10685  11.089  < 2e-16 ***
log_fuel     0.16225    0.08522   1.904   0.0585 .  
log_cruise   1.01941    0.19163   5.320 2.93e-07 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1923 on 188 degrees of freedom
Multiple R-squared:  0.9413,	Adjusted R-squared:  0.9394 
F-statistic: 502.6 on 6 and 188 DF,  p-value: < 2.2e-16

The passenger variable was removed as it was marginally insignificant. 
However, removing it led to a slight decrease in the adjusted R-squared value, which is expected since a predictor was removed. 
The number of passengers could still be relevant depending on the plane's intended use. 
For instance, the plane may be designed for personal or family use, where the number of passengers could affect its appeal and price. 
No significant changes were observed in the other coefficients.

```

Next regression model, if necessary:

```

lm_model_9 <- lm(data = airplane_full,
+     formula = log_price ~ log_age + tdrag + log_horse + log_fuel + log_cruise )
> summary(lm_model_9)

Call:
lm(formula = log_price ~ log_age + tdrag + log_horse + log_fuel + 
    log_cruise, data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.47869 -0.12981 -0.01332  0.11582  0.56832 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  4.81143    0.51266   9.385  < 2e-16 ***
log_age     -1.56455    0.06322 -24.749  < 2e-16 ***
tdrag       -0.35166    0.06534  -5.382 2.17e-07 ***
log_horse    1.18384    0.10763  10.999  < 2e-16 ***
log_fuel     0.16284    0.08585   1.897   0.0594 .  
log_cruise   0.74080    0.12826   5.776 3.11e-08 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1937 on 189 degrees of freedom
Multiple R-squared:  0.9401,	Adjusted R-squared:  0.9385 
F-statistic: 593.6 on 5 and 189 DF,  p-value: < 2.2e-16

The fixgear variable was removed as it was marginally insignificant. 
However, removing this variable caused a slight decrease in the adjusted R-squared value, suggesting that fixgear might still play a role in predicting price. 
The type of gear, whether fixed or retractable, could influence the price by affecting performance or requiring additional equipment such as hydraulic systems. 
Additionally, no significant changes were observed in the coefficients of the other variables.

```

Next regression model, if necessary:

```
lm_model_10 <- lm(data = airplane_full,
+     formula = log_price ~ log_age + tdrag + log_horse + log_cruise )
> summary(lm_model_10)

Call:
lm(formula = log_price ~ log_age + tdrag + log_horse + log_cruise, 
    data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.51552 -0.13447 -0.00468  0.11952  0.60763 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  4.68463    0.51174   9.154  < 2e-16 ***
log_age     -1.58088    0.06305 -25.072  < 2e-16 ***
tdrag       -0.35481    0.06577  -5.395 2.02e-07 ***
log_horse    1.31011    0.08515  15.386  < 2e-16 ***
log_cruise   0.77756    0.12765   6.091 6.10e-09 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.195 on 190 degrees of freedom
Multiple R-squared:  0.939,	Adjusted R-squared:  0.9377 
F-statistic: 731.1 on 4 and 190 DF,  p-value: < 2.2e-16

The removal of the marginally insignificant variable, log_fuel, results in a decrease in the adjusted R-squared value.
This suggests that log_fuel might still have an influence on the price. 
The rationale behind this is that larger fuel volumes allow for longer distances and higher weight capacity, which may be critical factors in determining the price of an airplane. 
Additionally, no significant changes were observed in the coefficients of the remaining variables.

```



e) Print the output from a ```summary``` of the regression results
of your final regression model.


```
Model 7
Call:
lm(formula = log_price ~ log_age + pass + fixgear + tdrag + log_horse + 
    log_fuel + log_cruise, data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.49050 -0.10900  0.01349  0.11515  0.54790 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  4.07670    0.87236   4.673 5.66e-06 ***
log_age     -1.52942    0.06359 -24.051  < 2e-16 ***
pass         0.05188    0.02149   2.414   0.0167 *  
fixgear     -0.14417    0.06717  -2.147   0.0331 *  
tdrag       -0.46649    0.07571  -6.161 4.32e-09 ***
log_horse    0.98598    0.13384   7.367 5.44e-12 ***
log_fuel     0.17238    0.08426   2.046   0.0422 *  
log_cruise   1.04191    0.18944   5.500 1.24e-07 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1898 on 187 degrees of freedom
Multiple R-squared:  0.9431,	Adjusted R-squared:  0.941 
F-statistic: 442.7 on 7 and 187 DF,  p-value: < 2.2e-16

This model retains the most significant variables, has a slightly better adjusted R-squared than other models, 
and does not add complexity by removing explanatoy predictors.
```

f) Finally, for each of the variables in the datasets, 
	list those that are positively related to airplane prices,
	negatively related to airplane prices, 
	and statistically unrelated to airplane prices. 


```

Positively:
pass: A higher number of passengers is correlated with higher airplane prices
log_horse: More horsepower is positively correlated with higher airplane prices
log_fuel: Greater fuel capacity is correlated to higher airplane prices
log_cruise: Higher cruise speed is correlated with higher airplane prices

Negatively:
log_age: Older airplanes are correlated to reduce prices
fixgear: Airplanes with fixed gear are correlated with lower prices than those with retractable gear
tdrag: Tail-dragger is associated with lower prices
wtop: Wing above the fusalage is correlated to reduce prices

log_ceiling: is negative but statistcally is close to zero and could be considered with no pos or neg relationship

```




## Part C: Version Control

### Question 5

Push your completed files to the ```final_exam``` folder 
in your private GitHub repository.