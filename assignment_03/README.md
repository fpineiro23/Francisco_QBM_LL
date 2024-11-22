# Assignment 3

Following the instructions in the document ```QMB6316_assignment_03.pdf``` above, 
enter your responses in the code blocks shown below.


In this exercise, we will follow an approach different than that taken in class. 
We will first estimate a model with our choices of functional form, then consider exclusions of insignificant variables from the full model. 
Note that this approach allows for inclusion of possibly irrelevant variables and avoids excluding any relevant variables. 


At each stage, use the best model that you have found so far, 
incorporating the findings from the answer to the previous question.




a. Estimate a regression model that uses all available variables, 
except for the indicator for an enclosed cab.
	Make sure to choose a reasonable transformation of the dependent variable, 
	such as the logarithmic transformation, if necessary.
	
```
Call:
lm(formula = log_saleprice ~ horsepower + age + enghours + diesel + 
    fwd + manual + johndeere + cab + spring + summer + winter, 
    data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.71960 -0.27081  0.06041  0.29064  0.93637 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  9.035e+00  1.179e-01  76.616  < 2e-16 ***
horsepower   4.287e-03  4.003e-04  10.709  < 2e-16 ***
age         -2.933e-02  3.876e-03  -7.569 6.31e-13 ***
enghours    -3.530e-05  1.038e-05  -3.400 0.000779 ***
diesel       3.188e-01  1.056e-01   3.019 0.002782 ** 
fwd          2.671e-01  6.371e-02   4.192 3.78e-05 ***
manual      -1.647e-01  6.732e-02  -2.447 0.015068 *  
johndeere    2.973e-01  7.846e-02   3.789 0.000187 ***
cab          6.899e-01  6.856e-02  10.063  < 2e-16 ***
spring      -1.015e-01  7.055e-02  -1.438 0.151552    
summer      -2.060e-01  6.917e-02  -2.978 0.003169 ** 
winter      -1.874e-01  7.743e-02  -2.420 0.016201 *  
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.4323 on 264 degrees of freedom
Multiple R-squared:  0.7609,	Adjusted R-squared:  0.751 
F-statistic:  76.4 on 11 and 264 DF,  p-value: < 2.2e-16

```

Does this seem to be a reasonable model, as opposed to using average tractor prices? 
	That is, is the R-squared or the R-bar-squared reasonably high?

```
The model appears reasonable, as the adjusted R-bar-squared of 0.751 indicates a good fit.
The significant variables also align well with theoretical expectations for factors influencing tractor prices.

```


b. Which variables seem to help explain used tractor prices? 
	Which have positive and negative relationships with tractor prices?
	Did you find any variables that do not have statistically significant coefficients under this specification?

```
Horsepower, disel, fwd being a measure of performance, is positively correlated to prices. 
Conversely, age and engine hours negatively correlated to prices as they reflect wear and tear. 
The manual transmission's negative coefficient may reflect lower desirability compared to automatic transmissions.
Deere and cab are positive coefficient reflecting desire for these attributes. 
Among seasonal variables, only 'summer' and 'winter' were some what significant, with negative effects on prices, suggesting lower demand during these periods.

```



c. Before making any reductions to your model, revise the model specification first
	by considering nonlinear specifications.
	A used tractor dealer tells you that overpowered used tractors are hard to sell, since they consume more fuel. 
      Tractor prices often increase with horsepower, up to a point, but beyond that they decrease. 
      To incorporate this advice, you create and include a variable for squared horsepower and include that in a new regression model. 
      

```
Call:
lm(formula = log_saleprice ~ horsepower + squared_horsepower + 
    age + enghours + cab + fwd + johndeere + spring + summer + 
    winter, data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.76852 -0.22863  0.05899  0.27633  0.75716 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)         8.991e+00  8.724e-02 103.054  < 2e-16 ***
horsepower          1.149e-02  1.066e-03  10.783  < 2e-16 ***
squared_horsepower -1.633e-05  2.256e-06  -7.239 4.91e-12 ***
age                -3.482e-02  3.480e-03 -10.006  < 2e-16 ***
enghours           -4.167e-05  9.702e-06  -4.295 2.46e-05 ***
cab                 4.769e-01  7.030e-02   6.784 7.62e-11 ***
fwd                 2.744e-01  5.900e-02   4.650 5.23e-06 ***
johndeere           2.750e-01  7.187e-02   3.826 0.000162 ***
spring             -1.147e-01  6.570e-02  -1.747 0.081881 .  
summer             -1.959e-01  6.443e-02  -3.041 0.002598 ** 
winter             -1.932e-01  7.191e-02  -2.687 0.007672 ** 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.4027 on 265 degrees of freedom
Multiple R-squared:  0.7918,	Adjusted R-squared:  0.7839 
F-statistic: 100.8 on 10 and 265 DF,  p-value: < 2.2e-16

```

  c.i) Hypothesize the signs for the coefficients on horsepower 
	under this scenario. 
		What should be the sign of the coefficient for horsepower? 
		What sign do you expect for squared horsepower?
   
```
According to the dealer's insight, overly powerful tractors become less desirable.
The hypothesized sign on the squared horsepower should be negative.
The hypothesized sign for horsepower should be positive.

```

  c.ii) Perform 1-sided t-tests of the hypotheses for each of the horsepower coefficients. 
That is, are the t-statistics higher than 1.96, with the same sign as you hypothesized?

```
The same hypothesized signs. 10.78 and 7.24 being higher than 1.96 indicate statistical significance.
horsepower          1.149e-02  1.066e-03  10.783  < 2e-16 ***
squared_horsepower -1.633e-05  2.256e-06  -7.239 4.91e-12 ***

```

  c.iii) Compare the model with or without the quadratic functional form for horsepower.
            Which model do you recommend? 
		Be sure to cite evidence to support your choice. 
		Specifically, check the four specification criteria: 
		statistical significant $t$-statistics, 
		an increase in R-squared, 
		a good theoretical justification, and 
		no large change in the other coefficients.

```
I would reccommed model with the quadratic functional form for horsepower.
The hypothesized signs align with theory and confirmed by the model.
Improvement in adjusted R^2 from 0.751 to 0.7839 and statistical significance above 2 of the quadratic term provide strong evidence for choosing this model.
No large change was experienced in other coefficients, some increased, and that perhaps shows how the model without quadradict tries to factor in inaccuracies.

```


d. Again, use the best model that results from the answer to the previous question to address further questions.
	Use the model you have so far to test that the time of year has no effect on the sale of tractors.
	That is, test whether the t-statistics on the seasonal indicators are statistical significant. 
	Is there evidence that tractor prices follow a seasonal pattern? 

```
The seasonal indicators 'summer' and 'winter' are somewhat statistically significant, suggesting that tractor prices are lower during these seasons. 
However, 'spring' is not significant, indicating no clear seasonal impact during that time.
This could suggest that tractor prices follow a seasonal pattern, potentially driven by demand fluctuations related to agricultural cycles.

```
	
	
e. Finally, consider another modification to your model. 
	Some say that John Deere tractors hold their value longer than other tractors. 
      This raises the question of whether an additional hour of use affects the value of a John Deere tractor 
	differently than for tractors of other brands. 
	You can test this by including an interaction with ```age:johndeere``` in the regression.
	
```
Call:
lm(formula = log_saleprice ~ horsepower + squared_horsepower + 
    age + enghours + cab + fwd + johndeere + spring + summer + 
    winter + age:johndeere, data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.78727 -0.22124  0.05925  0.26841  0.76405 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)         9.001e+00  8.837e-02 101.852  < 2e-16 ***
horsepower          1.155e-02  1.069e-03  10.798  < 2e-16 ***
squared_horsepower -1.636e-05  2.258e-06  -7.247 4.69e-12 ***
age                -3.556e-02  3.628e-03  -9.801  < 2e-16 ***
enghours           -4.227e-05  9.745e-06  -4.337 2.06e-05 ***
cab                 4.786e-01  7.040e-02   6.798 7.06e-11 ***
fwd                 2.747e-01  5.905e-02   4.652 5.20e-06 ***
johndeere           1.854e-01  1.422e-01   1.304  0.19335    
spring             -1.200e-01  6.615e-02  -1.814  0.07077 .  
summer             -1.998e-01  6.470e-02  -3.088  0.00223 ** 
winter             -1.943e-01  7.199e-02  -2.699  0.00741 ** 
age:johndeere       5.114e-03  7.001e-03   0.731  0.46571    
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.4031 on 264 degrees of freedom
Multiple R-squared:  0.7922,	Adjusted R-squared:  0.7835 
F-statistic:  91.5 on 11 and 264 DF,  p-value: < 2.2e-16

```

Test the hypothesis, at the 5 percent level of significance, that the slope for engine hours differs by brand. 

Does an additional hour of use affect the price of a John Deere tractor
differently than tractors of other brands?
	
```
The interaction term between 'age' and 'John Deere' suggests a slower depreciation rate for John Deere tractors. 
However, the term is not statistically significant, 0.731 is not greater than 2, so we cannot conclude that additional engine hours impact John Deere tractors differently than other brands.

```
	
	
