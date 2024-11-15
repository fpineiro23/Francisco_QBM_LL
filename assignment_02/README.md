# Assignment 2

Complete the exercise described in the pdf above and enter your answers in 
the spaces below.

## Running the Script as Given

Run the entire script and compare 
the output from ```summary(lm_full_model)```, 
which includes all variables, 
with that from ```summary(lm_no_damage)```, 
which omits the damage indicator. 
If there are no cars with damage in your simulation, 
run the script again to take another draw.


a. Copy and paste the regression model estimates after the commands
```summary(lm_full_model)``` and ```summary(lm_no_damage)```. 

```
Call:
lm(formula = car_price ~ mileage + accident + damage, data = car_data)

Residuals:
   Min     1Q Median     3Q    Max 
-14086  -2440    566   2503   8269 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  4.548e+04  2.470e+03  18.410  < 2e-16 ***
mileage     -1.334e-01  4.586e-02  -2.908  0.00451 ** 
accident    -3.629e+03  8.442e+02  -4.299 4.12e-05 ***
damage      -1.985e+04  2.410e+03  -8.236 8.97e-13 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 3998 on 96 degrees of freedom
Multiple R-squared:  0.5474,	Adjusted R-squared:  0.5332 
F-statistic:  38.7 on 3 and 96 DF,  p-value: < 2.2e-16

Call:
lm(formula = car_price ~ mileage + accident, data = car_data)

Residuals:
     Min       1Q   Median       3Q      Max 
-21004.7  -2080.0    940.5   3228.2   9613.8 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  4.727e+04  3.198e+03  14.781  < 2e-16 ***
mileage     -1.673e-01  5.936e-02  -2.819  0.00583 ** 
accident    -5.194e+03  1.069e+03  -4.859 4.53e-06 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 5196 on 97 degrees of freedom
Multiple R-squared:  0.2275,	Adjusted R-squared:  0.2116 
F-statistic: 14.28 on 2 and 97 DF,  p-value: 3.653e-06

```


b. Compare the estimated coefficient for ```ACCIDENT``` 
with and without the damage variable. 
How does this relate to the coefficient for ```DAMAGE```?

```
The estimated coefficient of damage decreases the value like accident.
The estimated coeffiecient without damage increases accident coefficient.
```


c. Compare the values of 
```Multiple R-squared``` and ```Adjusted R-squared``` for the two models. 
Which model do you recommend (pretending that you don't know the true model)? 

```
The model that includes damage, has a higher Adjusted R-squared representing a\
more accurate model when compared to missing damage.
```




## Running the Script after Modification


d. Copy and paste the new regression model estimates after the commands
```summary(lm_full_model)``` and ```summary(lm_no_damage)```. 

```
Call:
lm(formula = car_price ~ mileage + accident + damage, data = car_data)

Residuals:
    Min      1Q  Median      3Q     Max 
-8545.1 -2976.9   246.7  2760.3  9946.8 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  5.051e+04  2.180e+03  23.167  < 2e-16 ***
mileage     -2.124e-01  4.136e-02  -5.135 1.48e-06 ***
accident    -5.032e+03  8.525e+02  -5.903 5.37e-08 ***
damage      -1.518e+04  1.738e+03  -8.733 7.82e-14 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 3920 on 96 degrees of freedom
Multiple R-squared:  0.6487,	Adjusted R-squared:  0.6377 
F-statistic: 59.08 on 3 and 96 DF,  p-value: < 2.2e-16

Call:
lm(formula = car_price ~ mileage + accident, data = car_data)

Residuals:
     Min       1Q   Median       3Q      Max 
-16396.7  -2775.3    268.7   3636.1  10952.3 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  5.148e+04  2.901e+03  17.744  < 2e-16 ***
mileage     -2.314e-01  5.504e-02  -4.204 5.84e-05 ***
accident    -7.366e+03  1.079e+03  -6.828 7.53e-10 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 5223 on 97 degrees of freedom
Multiple R-squared:  0.3696,	Adjusted R-squared:  0.3566 
F-statistic: 28.43 on 2 and 97 DF,  p-value: 1.918e-10

```


e. For this new set of regressions, compare the estimated coefficient 
for ```ACCIDENT``` with and without the damage variable. 
How does this relate to the new coefficient for ```DAMAGE```?

```
Damage and accidents are directly correlated. Without damage varible,
the accident coeffiecient increases.
```


f. Compare the values of 
```Multiple R-squared``` and ```Adjusted R-squared``` for the two models. 
Now which model do you recommend (pretending that you don't know the true model)? 

```
The adjusted R-square has increased more in the model including damage.
This is the recommended model.
```

