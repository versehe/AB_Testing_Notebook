## Hypothesis testing
Hypothesis test is about making decisions using data.                  
```Null Hypothesis H<sub>0</sub>```: Null Hypothesis is assumed to be true until statistical evidence rejects it.            
```Alternative Hypothesis H<sub>a</sub>```: This usually is our research interest, we want to prove it makes a difference than normal.    
Through the test, if we draw a conclusion of H<sub>0</sub> is true, then we accept null; if we draw a conclusion of H<sub>a</sub> is true, then we reject null. 

### Type 1 and Type 2 Error
```Type 1 Error```:we shouldn't reject null but we did, we draw a conclusion of H<sub>a</sub> but it's actually H<sub>0</sub>. This is the worst because we think it will make a difference but it's actually not going to happen.                           
```Type 2 Error```:failed to reject null, we draw a conclusion of H<sub>0</sub> but it's actually H<sub>a</sub>. In this case, there is actually a difference but we didn't notice it.

### Confidence Level
We will need to choose a level of Type 1 Error that we can tolerate, this is the ```Confidence Level```. For example, if we run the test 100 time, and we want only 5 times of result fails into Type 1 Error, then our confidence level will be 5%, and the z score will be around 1.645 (If it's t test, then the t value will depends on the degree of freedom). Once we decide the confidence level, we could get the confidence inteval and see if it fails into it.      
<strong><ins>Please note the confidence level could appy to either 1 tail or 2 tails test</ins></strong>, depends on what kind of hypothesis you are getting. If you are doing a two tails test, make sure divide the confidence level by 2 in order to get the two tails.                       
If you are doing a one tail test, then you would only need 1 side bound. In this case, you may consider to reverse the process and get the T test value.
                 

### T test
An alternative way to test the significance is t test. Basically, it reverse the process of getting confidence inteval, calculate the t value and compare with the confidence level. As we already know, when sample size goes large, the difference between t value and z score will be minimum.        

Z = (X - μ)/SE= (X - μ)/{σ/SQRT(n)}                          
                                  
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/02.%20Distribution/normal%20distribution.png)


#### Two Group T test
H<sub>0</sub>:μ<sub>1</sub>=μ<sub>2</sub>     
H<sub>1</sub>:μ<sub>1</sub>≠μ<sub>2</sub> (2 tails case)   
For two groups t test, the common assumption is whether they have same mean, so expected value will be 0. We will use pooled Standard Error in this case.            
Pooled standard error = SQRT( {(n1-1)*STD1 +(n2-1)*STD2}/(n1+n2-2) )


### P Value
P-value is the probability of null hypothesis is true. If P-value is smaller than confidence level, then null hypothesis is unlikely to be true. So you can reject null hypothesis. It's an easy way to measure hypothesis test result. The basic idea is assuming nothing happens to our sample, then analyze how unusual the result is if null hypothesis is true.            
Another way to think about P value is to treat it as the edging confidence level (the smallest  that you will still reject the null hypothesis). For example, if P value is 4.9%, then it's telling me I will need to reject the null hypothesis on 5% confidence level. 
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/04.%20Hypothesis%20Testing//p-value.png)

### Power / Sensitivity
Type II error(Beta)：fail to reject null when the alternative is true.          
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/04.%20Hypothesis%20Testing//type2error.jpg)           
```Power = 1 - Beta```, it indicates the probablity of rejecting null when alternative is true, it's a good thing.                     
Because we paid most attention to minimize Type I error, we usually don't have too much flexibility on Sensitivity. We usually consider this during designing the AB test,  we could pick a large enough sample size to make sure the power is strong enough to detect the difference. when sample set is large enough,beta will be small, and power should reach close to 1. 

