Some probability distributions are so important that we need to internalize their characteristics. We will cover a few the most important probability distributions here. 


## Bernoulli distribution: simplest version of Binomial Distribution
Bernoulli distribution is the discrete probability distribution of a random variable which takes the value 1 with probability p and the value 0 with probability q = 1 − p. (Example: flip a coin)

P(x) = p<sup>x</sup>(1-p)<sup>(1-x)</sup>             
       P(0) = 1-p               
       P(1) = p               
Mean: p                  
Variance: p(1-p)                    


## Binomial Distribution
Binomial Distribution mass function is the sum of x<sub>1</sub> to x<sub>n</sub> Bernoulli distribution.

P(x) = C<sup>n</sup><sub>x</sub> * p<sup>x</sup>(1-p)<sup>(n-x)</sup>   独立重复试验       
C<sup>n</sup><sub>x</sub> = n!/x!(n-x)!  排列组合

## Normal Distribution
Normal Distribution is one of the most common distribution, it also calls Gaussian Distribution or bell curve. The mean of normal distribution is μ and variance of normal distribution is σ<sup>2</sup>.             
X ~ N(μ,σ<sup>2</sup>)                  
When mean u = 0, and standard deviation σ = 1, we call it standard normal distribution.          
Z ~ N(0,1)

We usually normalize a bell curve to standard normal distribution.   
Z = (X - μ)/σ ~ N(0,1)            
When it needs to convert back,             
N = Z*σ + μ ~ N(μ,σ<sup>2</sup>)         

### Facts to remember about standard normal distribution
* standard deviation range
   * the range of standard deviation (-1,1) engage about 68% of standard normal distribution
   * the range of standard deviation (-2,2) engage about ```95%``` of standard normal distribution, for normal distribution, the range is (u-2σ,u+2σ)
   * the range of standard deviation (-3,3) engage about 99% of standard normal distribution
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/02.%20Distribution/normal%20distribution.png)

* percentile
   * 0 is about the 50th of standard normal distribution
   * 1.28 is about the 90th of standard normal distribution
   * 1.645 is about the 95th of standard normal distribution
   * ```1.96``` is about the 97.5th of standard normal distribution, for normal distribution, the value is u + 1.96 * σ
   * 2.33 is about the 99th of standard normal distribution
   
That is to say, when we apply a range of (u-1.96 σ,u +1.96 σ), we get around 97.5th percentile - 2.5th percentile,which is around 95% in the middle (around mean u). We use this confidence inteval a lot in A/B test.   
  

## Poisson Distribution
Poisson Distribution might be the second most commonly used distribution after normal distribution, it has a deep connection with Multi-nonimals, Binonimals and Bernoullis.
P(x) = λ<sup>x</sup>e<sup>-λ</sup>/x!        ,where x is non-negative integers             
```mean``` is λ, and ```variance``` is also λ.           

![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/02.%20Distribution/Poisson%20Distribution.png)                        
As you can see in the graph, when lambda λ lager than 200, it will approximates to normal distribution.
 
* where to use Poisson Distribution?
   * a good candidate to model count data, especially when count is unbounded
   * model survival data
   * model rates           
   X ~ P(λ*t) ,where 
      * λ = E(x/t) is the expected rate, or count per unit of time                          
      * t stands for total monitor time                  
   for example, if average rate is 2.5, and we want to know what's the possibility of a count after 5 hours, then lambda = 2.5*5


   * default model of contingency table. Contingency table, so called Crosstab, is used in statistics to summarize the relationship between several categorical variables. A contingency table is a special type of frequency distribution table, where two variables are shown simultaneously. For example, if it's a male dog, it will count 1 in first cell below.
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/02.%20Distribution/contingency%20table.jpg)    
   * approximating Binomial Distribution when n is large and p is small         
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/02.%20Distribution/Poisson%20approximation%20to%20Binomial%20Distribution.PNG)    
