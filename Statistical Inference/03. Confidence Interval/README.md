## Asymptotics
Asymptotics means that sample size limits to infinity. It forms the basis of frequency interpretation of probability. For example, if we flip a coin for infinitely many times, we would get exactly 50% heads. The property of this called Law of Large Number.


### Law of Large Number
Law of Large Number(LLN) says the sample mean is consistent to the population mean if you repeat the experiment infinite times. So does sample variance and sample std.

### Central Limit Theorem
Central Limit Theorem(CLT) states that the distribution of ```sample means``` approximates a normal distribution as the sample size becomes larger, regardless of the population distribution shape.                    
   

For example, we have a normal distribution Z ~ N(u,σ<sup>2</sup>). As we know, the expected value x̅ of an mean distribution is still the population mean u, and we call the standard deviation of this mean distribution as standard error SQRT(σ2/n). When sample size n is large enough, then variance will become very small. This normal distribution Z ~ N(u,σ<sup>2</sup>/n) becomes close enough to standard normal distribution Z  ~ N(0,1). 

Normalize it to standard normal: Z = (x̅ - μ)/sqrt(σ<sup>2</sup>/n) ~ N(0,1)




## Confidence Interval
A pratical implementation of CLT is confidence interval. If I know the expected value of population mean and its variance, I could backtrack the area where sample mean should falls into.                   

For example, if I want 95% confindence level, the Confidence Interval would be (x̅ - 1.96 * (σ/SQRT(n)) , x̅ + 1.96 * (σ/SQRT(n)) ). In other word,           
```upper bound =  x̅ + z score * standard error```                
```lower bound = x̅ - z score * standard error```                     
BTW, if we are doing a one-tail test on 95% confindence level, Alpha will be 1.645 other than 1.96.
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/02.%20Distribution/normal%20distribution.png)



## T Distribution Confidence Interval    
T Distribution always has longer tails than normal distribution, so it fits better in small samples. Unlike normal distribution using mean and variance to define the scale, t distribution only need 1 parameter, the degree of freedom ```(n-1)```, and it always centers at 0. As the sample n increase, it makes smaller impacts to the degree of freedom, thus it becomes more like normal distribution.                      

T Confidence Interval: ```(x̅ - t value * standard error ,  x̅ + t value * standard error)```.It's similar as normal disbution, just simply replace the z score by t score.                     


T interval only works well with symmetric data. If the distribution is skewed, it doesn't make sense to center the interval at mean. In this case, consider using log to take care of the skewness or try to create bootstrap confidence interval.


### Compare Two Independent Groups using T Confidence Interval   
Let's say we are comparing means from 2 different groups with sample sizes, and we want to know if these 2 groups have different mean. Because we are now looking at 2 independent groups, not single group at different time, we can't use traditional paired t test in this case. Now we need a new technique called ```Pooled T test Confidence Interval```.     
Paired T Confidence Interval upper bound = x̅ + t value * standard error                           
```Pooled T Confidence Interval``` upper bound = (mean1 - mean2) + t value<sub>n1+n2-2</sub> * ```Pooled standard error``` * (1/n1＋1/n2)<sup>1/2</sup>　  
degree of freedom: n1+n2-2
```Pooled standard error``` =  SQRT( {(n1-1)*STD1 +(n2-1)*STD2}/(n1+n2-2)  )      
* If interval are all negative, then it tells us group 1 has significant lower mean than group 2.              
* If the final interval across 0, then it might have no signifcant difference.         

Or, you just simply reverse the process. Calculate the t value and see if it falls into the tail.
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/pooled%20t%20value.PNG)     
