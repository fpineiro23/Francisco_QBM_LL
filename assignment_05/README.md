
# Assignment 5


Continue the in-class exercise using the script 
```data_mining_A5.R``` in RStudio, 
which is a modified version of the script 
```data_mining_demo.R```.  
In this exercise, we generate simulated data for car prices, 
which depend on mileage, 
whether the car has been in an accident, 
and whether the car has sustained major structural damage, 
which can happen only as a result of an accident. 



Run the entire script and observe the output from the 
series of models.


		
a) Verify that damage occurs in both the samples. 
	Observe the output under the code blocks in lines 123-139
	to verify that the bottom right numbers 
	(the number of observations with accidents with damages) are not zero.
	If one of these bottom-right numbers is zero, run the script again. 
	
```

summary(car_data)
    obsn_num        car_price        mileage         accident       damage     
 Min.   :  1.00   Min.   : 8205   Min.   :27318   Min.   :0.0   Min.   :0.000  
 1st Qu.: 50.75   1st Qu.:34013   1st Qu.:43863   1st Qu.:0.0   1st Qu.:0.000  
 Median :100.50   Median :37558   Median :52600   Median :0.0   Median :0.000  
 Mean   :100.50   Mean   :36266   Mean   :51057   Mean   :0.4   Mean   :0.075  
 3rd Qu.:150.25   3rd Qu.:41214   3rd Qu.:58462   3rd Qu.:1.0   3rd Qu.:0.000  
 Max.   :200.00   Max.   :50748   Max.   :76089   Max.   :1.0   Max.   :1.000  
    epsilon           mileage_1       mileage_2       rainfall_1     rainfall_2   
 Min.   :-9970.54   Min.   :18732   Min.   :14407   Min.   :0.00   Min.   :0.000  
 1st Qu.:-2623.11   1st Qu.:42726   1st Qu.:42307   1st Qu.:0.00   1st Qu.:0.000  
 Median : -111.98   Median :51166   Median :52363   Median :0.00   Median :0.000  
 Mean   :  -23.06   Mean   :51124   Mean   :50838   Mean   :0.23   Mean   :0.265  
 3rd Qu.: 2785.00   3rd Qu.:59591   3rd Qu.:59270   3rd Qu.:0.00   3rd Qu.:1.000  
 Max.   : 8270.18   Max.   :73736   Max.   :80941   Max.   :1.00   Max.   :1.000  
   rainfall_3     rainfall_4      rainfall_5     rainfall_6      rainfall_7  
 Min.   :0.00   Min.   :0.000   Min.   :0.00   Min.   :0.000   Min.   :0.00  
 1st Qu.:0.00   1st Qu.:0.000   1st Qu.:0.00   1st Qu.:0.000   1st Qu.:0.00  
 Median :0.00   Median :0.000   Median :0.00   Median :0.000   Median :0.00  
 Mean   :0.25   Mean   :0.255   Mean   :0.24   Mean   :0.275   Mean   :0.18  
 3rd Qu.:0.25   3rd Qu.:1.000   3rd Qu.:0.00   3rd Qu.:1.000   3rd Qu.:0.00  
 Max.   :1.00   Max.   :1.000   Max.   :1.00   Max.   :1.000   Max.   :1.00  
   rainfall_8      rainfall_9     rainfall_10    rainfall_11     rainfall_12   
 Min.   :0.000   Min.   :0.000   Min.   :0.00   Min.   :0.000   Min.   :0.000  
 1st Qu.:0.000   1st Qu.:0.000   1st Qu.:0.00   1st Qu.:0.000   1st Qu.:0.000  
 Median :0.000   Median :0.000   Median :0.00   Median :0.000   Median :0.000  
 Mean   :0.285   Mean   :0.225   Mean   :0.28   Mean   :0.255   Mean   :0.195  
 3rd Qu.:1.000   3rd Qu.:0.000   3rd Qu.:1.00   3rd Qu.:1.000   3rd Qu.:0.000  
 Max.   :1.000   Max.   :1.000   Max.   :1.00   Max.   :1.000   Max.   :1.000  
  rainfall_13     rainfall_14     rainfall_15     rainfall_16    rainfall_17  
 Min.   :0.000   Min.   :0.000   Min.   :0.000   Min.   :0.00   Min.   :0.00  
 1st Qu.:0.000   1st Qu.:0.000   1st Qu.:0.000   1st Qu.:0.00   1st Qu.:0.00  
 Median :0.000   Median :0.000   Median :0.000   Median :0.00   Median :0.00  
 Mean   :0.265   Mean   :0.245   Mean   :0.225   Mean   :0.23   Mean   :0.29  
 3rd Qu.:1.000   3rd Qu.:0.000   3rd Qu.:0.000   3rd Qu.:0.00   3rd Qu.:1.00  
 Max.   :1.000   Max.   :1.000   Max.   :1.000   Max.   :1.00   Max.   :1.00  
  rainfall_18    rainfall_19     rainfall_20   
 Min.   :0.00   Min.   :0.000   Min.   :0.000  
 1st Qu.:0.00   1st Qu.:0.000   1st Qu.:0.000  
 Median :0.00   Median :0.000   Median :0.000  
 Mean   :0.29   Mean   :0.285   Mean   :0.245  
 3rd Qu.:1.00   3rd Qu.:1.000   3rd Qu.:0.000  
 Max.   :1.00   Max.   :1.000   Max.   :1.000  
> 
> # Check that damages occurred only in accidents:
> table(car_data[, 'accident'], car_data[, 'damage'])
   
      0   1
  0 120   0
  1  65  15
> # Data errors are the largest cause of problems in model-building.
> 
> # Check the subsamples for estimation and testing.
> # Estimation sample:
> table(car_data[obsns_for_estimation, 'accident'],
+       car_data[obsns_for_estimation, 'damage'])
   
     0  1
  0 58  0
  1 24 10
> # Testing sample:
> table(car_data[!obsns_for_estimation, 'accident'],
+       car_data[!obsns_for_estimation, 'damage'])
   
     0  1
  0 62  0
  1 41  5
> # ! means 'not'.
> # So, !obsns_for_estimation means to include only the
> # observations left out for testing the model.

```

		
b) Copy and paste the table of selected models and R-squared values, 
	under the command ```print(best_models)``` on line 315. 
	
```

print(best_models)
   num_vars best_new_variable R2_in_sample R2_out_sample
1         1            damage    0.6993235     0.4965911
2         2          accident    0.7691590     0.5764086
3         3         mileage_1    0.8062106     0.6501913
4         4       rainfall_19    0.8100987     0.6461070
5         5         mileage_2    0.8113899     0.6573787
6         6       rainfall_10    0.8120805     0.6280710
7         7        rainfall_4    0.8121276     0.6158574
8         8        rainfall_6    0.8119188     0.6202205
9         9        rainfall_5    0.8105629     0.6189952
10       10       rainfall_18    0.8091220     0.6179498
11       11       rainfall_14    0.8072626     0.6097358
12       12        rainfall_3    0.8055132     0.6073182
13       13       rainfall_13    0.8035974     0.6071133
14       14        rainfall_9    0.8015012     0.6135035
15       15        rainfall_8    0.7991621     0.6120743
16       16        rainfall_1    0.7966588     0.6122527
17       17        rainfall_2    0.7941170     0.6130807
18       18       rainfall_16    0.7914447     0.6138438
19       19       rainfall_12    0.7885792     0.6127943
20       20       rainfall_17    0.7856283     0.6130820
21       21       rainfall_15    0.7825821     0.6137957
22       22        rainfall_7    0.7794446     0.6146673
23       23       rainfall_11    0.7762051     0.6142062
24       24       rainfall_20    0.7728670     0.6137782

```

		
c) Compare the models according to the in-sample ```R-bar-squared``` 
		under the column ```R2_in_sample```. 
		Which model is best under this criterion? 
		The variables in the model are listed in the column ```best_new_variable```
		up to the row of the chosen model. 

```
Up to 7 varibles
num_vars best_new_variable R2_in_sample R2_out_sample
1         1            damage    0.6993235     0.4965911
2         2          accident    0.7691590     0.5764086
3         3         mileage_1    0.8062106     0.6501913
4         4       rainfall_19    0.8100987     0.6461070
5         5         mileage_2    0.8113899     0.6573787
6         6       rainfall_10    0.8120805     0.6280710
7         7        rainfall_4    0.8121276     0.6158574

```
		
d) Compare the models according to the out-of-sample ```R-bar-squared``` 
		under the column ```R2_out_sample```. 
		Which model is best under this criterion? 
		The variables in the model are listed in the column ```best_new_variable```
		up to the row of the chosen model. 

```
Up to 5 variables.
 num_vars best_new_variable R2_in_sample R2_out_sample
1         1            damage    0.6993235     0.4965911
2         2          accident    0.7691590     0.5764086
3         3         mileage_1    0.8062106     0.6501913
4         4       rainfall_19    0.8100987     0.6461070
5         5         mileage_2    0.8113899     0.6573787

```
		
e) Compare the differences between the two models.
		Do any variables appear in one model and not the other?
		Which model do you recommend on the basis of this data? 
		Is your recommended model the same as the true model? 



```
Yes, more varibles are included in the in-sample varibles Using the out-sample
data indicates that the less varibles will likely represent the true model.
I would recommend the model with the out of sample varibles and this model
is not the same as the true model; as the true model would not include the extra
that only increase the adjusted R-Square value marginaly.

 num_vars best_new_variable R2_in_sample R2_out_sample
1         1            damage    0.6993235     0.4965911
2         2          accident    0.7691590     0.5764086
3         3         mileage_1    0.8062106     0.6501913
4         4       rainfall_19    0.8100987     0.6461070
5         5         mileage_2    0.8113899     0.6573787

```
