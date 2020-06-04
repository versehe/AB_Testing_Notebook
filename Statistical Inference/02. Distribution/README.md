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
