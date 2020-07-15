## Asymptotics
Asymptotics means that sample size limits to infinity. It forms the basis of frequency interpretation of probability. For example, if we flip a coin for infinitely many times, we would get exactly 50% heads. The property of this called Law of Large Number.


### Law of Large Number
Law of Large Number(LLN) says the sample mean is consistent to the population mean if you repeat the experiment infinite times. So does sample variance and sample std.

### Central Limit Theorem
Central Limit Theorem(CLT) states that as sample size increase, random variable roughly becomes standard normal. 

For example, we have a normal distribution Z ~ N(u,σ<sup>2</sup>). As we know, the expected value x̅ of an mean distribution is still the population mean, and we call the standard deviation of this mean distribution as standard error SQRT(σ2/n). This mean distribution should also follow the same normal distribution.                
Z = (x̅ - μ)/sqrt(σ<sup>2</sup>/n)     
When sample size n is large enough, then variance will be very small. This normal distribution Z ~ N(u,σ<sup>2</sup>/n) becomes close enough to standard normal distribution(Z ~ N(0,1)). Same thing happens to binomial distribution and others.

## Confidence Interval
A pratical implementation of CLT is confidence interval. If I know the expected value of population mean and its variance, I could backtrack the area where sample mean should falls into.                   

For example, if I want 95% confindence level, the Confidence Interval would be (x̅ - 1.96 * (σ/SQRT(n)) , x̅ + 1.96 * (σ/SQRT(n)) ). In other word,           
```upper bound =  x̅ + z score * standard error```                
```lower bound = x̅ - z score * standard error```               

![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/02.%20Distribution/normal%20distribution.png)
