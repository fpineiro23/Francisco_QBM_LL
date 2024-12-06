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
formula = log_price ~ log_age + pass + wtop + fixgear + tdrag + log_horse + log_fuel + log_cruise )

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
Call:
lm(formula = log_price ~ log_age + fixgear + tdrag + log_horse + 
    log_fuel + log_ceiling + log_cruise, data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.46839 -0.11055 -0.01486  0.11283  0.56699 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  3.60114    1.00767   3.574 0.000448 ***
log_age     -1.56382    0.06292 -24.855  < 2e-16 ***
fixgear     -0.12727    0.07176  -1.773 0.077791 .  
tdrag       -0.41605    0.08149  -5.105 8.09e-07 ***
log_horse    1.18812    0.10833  10.968  < 2e-16 ***
log_fuel     0.16152    0.08552   1.889 0.060474 .  
log_ceiling -0.01823    0.08891  -0.205 0.837725    
log_cruise   1.02850    0.19716   5.217 4.81e-07 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1928 on 187 degrees of freedom
Multiple R-squared:  0.9413,	Adjusted R-squared:  0.9391 
F-statistic: 428.6 on 7 and 187 DF,  p-value: < 2.2e-16

The variable wtop is statistically insignificant and should be removed as the adjusted 
R-squared value decreased only by little bit, when buying aiplanes people consider low wings and 
top wings for performance and safety purposes but it's not the main factor, 
and no large change in other coefficients were observed.

```

Next regression model:

```
summary(lm_model_7)

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

The log_ceiling variable is statistically insignificant and should be removed from the 
regression, as the adjusted R-squared value increased when removed, the maximum
flying hight of an airplane is important but typically based on the plane is on
range and commercial planes are the one concern about really heigh altitudes, 
and no large change on other variables were observed.
```

Next regression model, if necessary:

```

Copy your regression results here.


```

Next regression model, if necessary:

```

Copy your regression results here.


```

Next regression model, if necessary:

```

Copy your regression results here.


```



e) Print the output from a ```summary``` of the regression results
of your final regression model.


```

Copy your final regression results here.


```

f) Finally, for each of the variables in the datasets, 
	list those that are positively related to airplane prices,
	negatively related to airplane prices, 
	and statistically unrelated to airplane prices. 


```

Enter your response here.


```




## Part C: Version Control

### Question 5

Push your completed files to the ```final_exam``` folder 
in your private GitHub repository.