## Hypothesis testing
Hypothesis test is about making decisions using data.                  
```Null Hypothesis H<sub>0</sub>```: Null Hypothesis is assumed to be true until statistical evidence rejects it.            
```Alternative Hypothesis H<sub>a</sub>```: This usually is our research interest, we want to prove it makes a difference than normal.    
Through the test, if we draw a conclusion of H<sub>0</sub> is true, then we accept null; if we draw a conclusion of H<sub>a</sub> is true, then we reject null. 

### Type 1 and Type 2 Error
```Type 1 Error```:we shouldn't reject null but we did, we draw a conclusion of H<sub>a</sub> but it's actually H<sub>0</sub>. This is the worst because we think it will make a difference but it's actually not going to happen.                           
```Type 2 Error```:failed to reject null, we draw a conclusion of H<sub>0</sub> but it's actually H<sub>a</sub>. In this case, there is actually a difference but we didn't notice it.

### Confidence Level
We will need to choose a level of Type 1 Error that we can tolerate, this is the ```Confidence Level```. For example, if we run the test 100 time, and we want only 5 times of result fails into Type 1 Error, then our confidence level will be 5%, and the z score will be around 1.645.       
<strong><ins>Please note the confidence level could appy to either 1 tail or 2 tails test</ins></strong>, depends on what kind of hypothesis you are getting.               

Once we decide the confidence level, we could get the confidence inteval and see if it fails into it.

### T test
An alternative way to test the significance is t test. Basically, it reverse the process of getting confidence inteval, calculate the z score (or t value if sample size is small) and compare with the confidence level. One thing should be aware: When doing two tails test, make sure divide the confidence level by 2 in order to get the two tails.                            
Z = (X - μ)/SE= (X - μ)/{σ/SQRT(n)}                                       
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/02.%20Distribution/normal%20distribution.png)
