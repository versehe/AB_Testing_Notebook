### What is Probability?      
Probability assigns a number between 0 and 1 to events to give a sense of the "chance" of the event. 

The probability of two things that cannot simultaneously occur(mutually exclusive) is the sum of their respective probabilities.     
P(A∪B) = P(A) + p(B)    
Otherwise, if these two things can happen simultaneously, the probability that at least one occurs is the sum of their probabilities minus their intersection.    
P(A∪B) = P(A) + p(B) - P(A∩B)    


### Random Variable
random variable is a numeric outcome of experiment. It could be ```Continous``` or ```Discrete```.  
* ```Probability Mass Function```: a function that takes any values that a discrete random variable can take, and simply assign the probability when it takes a specific value. (Example: roll a dice)
     * the probality must be larger than or equal to 0.(P(1)=P(2)=P(3)=P(4)=P(5)=P(6)=1/6)
     * the sum of the probalities of all possible value must equal to 1.(P(1) + P(2) +  P(3) +  P(4) +  P(5) + P(6) = 1.)       
* ```Probability Density Function```: a function that use area to reflect the possibility of a range of continous random variable. Because it use area to indicate possibilty, the possibility of a specific random variable is going to be 0, sicne the area of a line is 0.(Example: normal distribution/bell curve)
     * the probality must be larger than or equal to 0 everywhere.
     * the sum of the probalities of all possible value must equal to 1.                                         
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/01.%20Probability/bell%20curve.PNG)         
### Cumulative Density Function and survival function
* ```Cumulative Density Function```, or ```quantile```,  returns the possibility that the random variable is less than or equal to the value x.        
F(x) = P(X <= x)    
* ```survival function``` returns the possibility that the random variable is greater than the value x.                    
S(x) = P(X > x)    


### Most famous Probability Mass Function: Bernoulli distribution
Bernoulli distribution is the discrete probability distribution of a random variable which takes the value 1 with probability p and the value 0 with probability q = 1 − p. (Example: flip a coin)               
* P(x) = θ<sup>x</sup>(1-θ)<sup>(1-x)</sup>                 
     * P(0) = 1-θ         
     * P(1) = θ              

### Conditional Probability
On the ground that the probability of event B happening is greater than 0, he probability of event A happens after event B happen can be written as:                 
P(A|B) = P(A∩B) /p(B)                      
If event A and B are independent, the probability of event A doesn't really relys on event B. Thus, it becomes:         
P(A|B) = P(A∩B) /p(B)  =  P(A)*P(B) /p(B) = P(A)       

### Bayes' Rule
It allows us to reverse the role of conditional set and get us the probability of the reversed set.              
```P(B|A) = P(A|B)*P(B) / P(A)```              
Or, P(B|A) =P(A|B)*P(B) / {P(A|B)*P(B)+ P(A|B<sup>c</sup>)*P(B<sup>c</sup>)}, where P(B<sup>c</sup>) is the probability of B not happen
#### Likelihood Ratio
P(B|A) =P(A|B)*P(B) / {P(A|B)*P(B)+ P(A|B<sup>c</sup>)*P(B<sup>c</sup>)}                  
P(B<sup>c</sup>|A) =P(A|B<sup>c</sup>)*P(B<sup>c</sup>) / {P(A|B)*P(B)+ P(A|B<sup>c</sup>)*P(B<sup>c</sup>)}      
since the denominator are same:                   
P(B|A)/P(B<sup>c</sup>|A) = P(A|B)*P(B) /P(A|B<sup>c</sup>)*P(B<sup>c</sup>)  = ( P(A|B)/P(A|B<sup>c</sup>)) * (P(B)/P(B<sup>c</sup>))              
thus, P(B|A)/P(B<sup>c</sup>|A) = ( P(A|B)/P(A|B<sup>c</sup>)) * (P(B)/P(B<sup>c</sup>))     
in other words:                   
```post test odds```  = ```Likelihood Ratio``` * ```pre test odds```          

### Expected Value
```Expected value```, or ```the mean of a random variable``` is the center of a distribution. We use the sample mean to estimate the population mean. If the distribution is discrete, then the expected value can be calculated as:         
E[x]= Σx*P(x)                       

If I roll a dice, the expected value is always 3.5; If I roll 2 dices and take the average, the expected value of this average distribution still remains the same. This is a great feature for us to estimate the population expected value from a sample.                           
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/Statistical%20Inference/01.%20Probability/roll_dice_example.PNG)  
*Note: this works to continous distribution too.

###  Variability
Variability measures how spread out a population is. We measure population variability with the sample ```variance``` or ```standard deviation```.             
Var(X) = Σ(x-μ)<sup>2</sup> = Σ(x<sup>2</sup>)- Σ(x)<sup>2</sup>, where μ stands for the mean of this ramdon variable          
STD(X) = SQRT(Var(X))                        
For Bernoulli distribution, the probability of happen is p, and probability of not happen q = 1-p         
Var(X) = p(1-p)

When estimate the sample variance from obeserved variance:
S<sup>2</sup>= Σ<sub>i-1</sub>（X<sub>i</sub>-x̅）<sup>2</sup>/n-1              
This sample variance also has a population distribution, the expected value of this distribution is the population variance. When we collect more sample variances, the distribution get more concentrate to the population variance, which is what we are trying to estimate.



###  Standard Error
We already know: The variance of a random variable itself is also a distribution, and the expected value of this distribution concentrates around the avarage of variance, σ<sup>2</sup>. Also, the expected value of an mean distribution is still the population mean. Thus, We could estimate the variance of population mean:              
Var(x̅) = σ<sup>2</sup>/n  
STD(x̅) = SQRT(σ<sup>2</sup>/n) = STD(x̅)/ SQRT(n)                     
We call the standard deviation of the mean distribution as ```standard error```. The more data we collect, this distribution is more concentrated, and standard error is more close to 0.              

While Variability measures how spread out a population is. Standard Error measures how spread out the expect value of a population, estimated by the expected value of the sample mean distribution. 

