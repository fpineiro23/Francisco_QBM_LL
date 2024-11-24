# Assignment 4

Complete the exercise described in the pdf above and enter your answers in 
the spaces below.

## Running the Script as Given

Run the entire script and observe the output from the simulation.
In particular, observe the statistics printed at the bottom.



a. Copy and paste the means and standard deviations from the output after the commands
```sapply(reg_results[, full_list_of_variables], mean)``` 
and ```sapply(reg_results[, full_list_of_variables], sd)```. 


```

sapply(reg_results[, full_list_of_variables], mean)
    intercept       mileage      accident        damage 
 4.991809e+04 -1.987199e-01 -4.958496e+03 -1.997181e+04 

sapply(reg_results[, full_list_of_variables], sd)
   intercept      mileage     accident       damage 
2.435930e+03 4.606231e-02 8.138124e+02 2.955795e+03

```

b. For each parameter, calculate the distance between the mean estimate and the true value, in terms of the number of standard deviations of that variable. 
The true values of the coefficients are listed in lines 74 to 78 in the script ```OLS_on_repeat_A4.R```.


```
(50000- 4.991809e+04)/2.435930e+03 = 0.03362576
(0.20+1.987199e-01)/4.606231e-02 = 8.656099
(5000+4.958496e+03)/8.138124e+02 = 12.23684
(20000+1.997181e+04)/2.955795e+03 = 3.5232

```


c. Now compare the average values of each of the estimated coefficients with their true values.
Are they biased or unbiased?
Keep in mind that with an unbiased estimator 
a difference of less than $2$ standard deviations could often happen by chance.


```

The estimators for mileage, accident, and damage are biased, with Z-scores exceeding 2 standard deviations, indicating significant deviation from true values.
Only the intercept is unbiased, as its Z-score falls within 2 standard deviations of the true value.

```



## Running the Script after Modification


d. Copy and paste the means and standard deviations from the output 
after the commands 
```sapply(reg_results[, full_list_of_variables], mean)```

and ```sapply(reg_results[, full_list_of_variables], sd)```.


```

> print('Average value of the coefficients are:')
[1] "Average value of the coefficients are:"
> sapply(reg_results[, full_list_of_variables], mean)
    intercept     mileage_1      accident        damage 
 4.402036e+04 -8.593771e-02 -4.841822e+03 -1.857325e+04 
> 
> # Calculate the standard deviation of the estimates.
> print('Standard Deviations of the coefficients are:')
[1] "Standard Deviations of the coefficients are:"
> sapply(reg_results[, full_list_of_variables], sd)
   intercept    mileage_1     accident       damage 
1.484228e+03 2.746176e-02 8.250728e+02 2.883077e+03

```


e. For each parameter, calculate the distance between the mean estimate and the true value, in terms of the number of standard deviations of that variable. 


```

(50000-4.402036e+04)/1.484228e+03 = 4.028788
(0.20+8.593771e-02)/2.746176e-02 = 10.41221
(5000+4.841822e+03)/8.250728e+02 = 11.92843
(20000+1.857325e+04)/2.883077e+03 = 13.3792

```


f. Now compare the average values of each of the estimates 
with their true values when the true 
```mileage``` is unobserved 
but inaccurate ```mileage_1``` is observed instead.
Are they biased or unbiased?
Again, keep in mind that with an unbiased estimator 
a difference of less than $2$ standard deviations could often happen by chance. 


```
All estimators are biased based on the Z-scores calculated.
None of the variables fall within 2 standard deviations of their true values.

```

