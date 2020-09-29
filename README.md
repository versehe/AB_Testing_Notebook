# AB_Testing_Notebook

### What is AB testing?
In a word, ab testing is an experiment that randomly split your users into 2 or multiple groups, and test whether your product new feature could hit a better performance. Users view original product/page are called ```Control group```, and users view new features are called ```Variation Group```. Generally, you don't want too many variations for a single test, because the more variations created, the higher possibility it could fall out of confidence interval.

### When not to use AB testing?
AB testing is great to test whether this feature could help improve your business goal or not. But it could'n tell you what else feature you should add. The experiment group needs to be radomly assigned, you need to worry about things like network effects. Also, if the user reaction is too long or hard to track, then you couldn't find a significant difference from your result.

For example:
* **I want to figure out what product I could add to my website.**      
  *AB testing can only tell you whether this product adding to your website will helps or not, it can't tell you what else product you could add. For this goal, you may design a customer survey and collect ideas.*
* **A car dealer try to prompt special coupon to attract repeative purchase or word of mouth.**      
  *Customer may not re-do their purchase in a short time, so you couldn't see a significant difference in short term. The target of your experimental group needs to have stronger reactions. For example, do a sales promption to customer visited recently or did test drive recently, see if this promption could attract them come back and buy.* 
* **Website logo change.**      
  *Users are surprisingly emotional to this kind of change. You may experience a downturn in short time, but this change is reversable, they may eventually come back. So the ab tesing result in short term might be false positive.*
* **Give cupcakes samples to a local communuity to test best flavor.**      
  *Your customers may have a strong impacts to each other, their opinions might not be truly idependent thoughts. You may want to give yout samples to customer individually.*

### Concerns in AB testing designing
1. **risk**: what risk your participants are taking? think about medicine experiments
2. **benefit**:what Even if the risk is minimal, will the results help imcrease your engagement/revenue?
3. **alternatives**: the fewer alternatives that participants have, the more likely they will still have to use your service.
4. **privacy**: you may want to collect and store anonymous data other than identified data. Anonymous data can be considered pseudonymous if it is stored with a randomly generated id

### Metric Definition
1. **define a high level metric**: it can be active users or revenues.
2. **define the deifinition of your metric**: what is "active"? a login, a view or a comment?
3. **choose measurements of your metric**: count of daily active users, average time spent or DAU/MAU ratio? In this example, it depends on you are looking for improvment of impressions or an improvment of truly engagement rate. Anyway, your metric should be sensetive to your experiment and robust in distribution.
4. **filter data**: detect spam and fraud data such as robot activities. Also, you might only conduct this ab test on web side, so you should filter out views from mobile apps.

* What metrics can't be measure?
  *  don't have access to this data
  *  takes too long to collect. e.g. re-purchase of a car

* one metric vs multiple metrics?
  *  generally single metric is eaiser to evaluate and avoid chaos. (type I error - false positive)
  *  if you have multiple metrics need to be evaluate, try to make it as a composite metric such as OEC(overall evaluation criterion). But the tricky part is how to set the weights of different metrics to this composite metric.

* Additional resource to collect data?
  *  user experience research: could only focus on small group of users, data are deep but less
  *  focused group: target a specific group of people, present to them and hear feedbacks. The issue is that you may hear less vocie than you expect, 1-2 loud voice could also affect others thoughts
  *  survey: you could collect a lot of data in this way, but what people said may differ from what they truly thought
  
### Common Metrics
* Engagement
  *  Count: DAU (daily active user),MAU (monthly active user) - how do you define active?
     * if the activity has significant weekly variation, consider MAU as 28 daya instead of 30 days
  *  Mean : average time spent, 90 percentile (long tail)
  *  Ratio: DAU/MAU ratio - truly engagement rate
* Revenue
  *  Mean : average $ spent per user, RPM (revenue per thousand query), cost per click
* Impression
  *  Ratio: CTR (click through rate) = # of click / # of page views in given time period
  *  Probablity: CTP (click through probablity) = # of unique visitors click/# of unique visitors view this page in given time period
  
### Confidence Interval
#### Normal Distribution: (for mean)
 * mean = (A1+A2+...+An)/n
 * standard error = sqrt(variance/n) = standard deviation /sqrt(n)
 * margin of error = z score * standard error
   * e.g. 95% confidence level, z value is 1.96
 * upper bound = mean + margin of error
 * lower bound = mean - margin of error

#### Binomial Distribution: (for probablity - binary, independent event) 
 * estimated probablity (p hat) = # users who click / # users who view page 
 * standard error = sqrt(p hat * (1 -p hat) / # users who view page)
 *  sanity check: if p hat * # users who view page  > 5 and (1 - p hat)* # users who view page  > 5, we can use normal distribution to find margin of error
 * margin of error = z score * standard error
 * upper bound = p hat + margin of error
 * lower bound = p hat - margin of error

### Form Hypothesis
 *  null hypothesis (H0): Control group
 *  alternative hypothesis (H1): Variation Group

### Design Experiment
* **business process**: analyze business process to understand the logic of business line, for each step of the business life cycle there will be a measurable subject be applied     
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/business%20process%20funnel.PNG)     
* **choose subject**: assign by event, by user or by cookie? consider about consistancy, privacy and if subjects and metrics are at the same level
  * event: it may gone if user reload the page, so only apply to user not visible changes
  * user id: user could have multiple accounts, it's also an identifier
  * anomyous id (cookie): user could switch from mobile to desktop, or from IE to firefox
  * divice id: only apply to mobile
  * IP address: changes when user switch location
* **choose population**: target to specific language/broswer group of users to avoid bias. After finishing experiment, you may want to re-run your experiment globally to make sure no un-intentional effects
  * cohort vs population: ```cohort``` is a group of user enter at same time who have shared experience, it improves stability but requies more samples because users could drop out. You only need cohort when you try to analyze things like user retention or engagement, where you need to know whether they are same users.
* **decide sample size**:、
  * ```baseline conversion rate```: the conversion rate value of our control group variation (variation A), you can look at historical data to determine it.
  * ```Minimum Detectable Effect```: the smallest relative change in conversion rate you are interested to detect between variations A and B conversion. For a product with large group of users, the difference could be 1% - 2%.
  * ```Estimated Standard Error```: if data don't affirm normal distribution/binoimal distribution, it might be hard to calculate SE. Try to use Bootstrap or Delta method to get an estimated standard error. 
  * choose ```statistical significance```(P Value): confidence level (alfa). Usually alfa is 5%, which means 95% of time it should fall in confidence interval
  * choose ```statistical power```: sensitivity (1 - beta). Usually beta is 20%, so power is 80%. If result falls in beta, it means no significant difference between ariations A and B.        
  ![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/true%20difference.png)             
     * if we feed more samples into experiment, the distribution will become sharper, then true difference area will expands.      
  ![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/more%20sample%20difference.png)    
* **random assign samples to groups**:
  * purified randomization
  * ```stratified randomization```: in order to aviod bias (gender/ages unequally assigned), firstly assign samples into different strata, then randomly assign them for each strata
  * ```cluster randomization```: first assign samples into different cluster by their similarity, then assign randomly from each cluster. We usually use this approach to aovid network effect
     * ```network effect```: user of a service has on the value of that product to others. When a network effect is present, the value of a product or service increases according to the number of others using it. (word of mouth)
  * ```cross-over randomization```: when sampel size is small, after first round test finished, wait until test result fades, then switch 2 groups over to do next round test.
* **decide experiment duration**:sample size matters could affect duration, if you select a small proportion of traffic to test, you may need to run longer in order to collect enough data. Also, take user learning effect into consideration, user may react irrational when first seeing a new change, but eventually they will perform different from when they just saw it. Not only duration, when to start your experiment is also critical. e.g. online shopping has a seasonality at year end, it could affect to result. 

### Evaluate Result
* sanity check: before analyze your experiment result, do some sanity check to make sure the results are in fact comparable.e.g. when evaluating the click through rate, the number of users who view the page shouldn't change significantly at the first place
* **T test**: figure out if your experiment has a statistical significance between the population mean and a hypothesized value
  * **t value** = mean difference between control group and variation group (d hat) / standard error    
![alt](https://github.com/versehe/AB_Testing_Notebook/blob/master/pooled%20t%20value.PNG)     
  * margin of error = z score * standard error
  * upper bound = d hat + margin of error
  * lower bound = d hat - margin of error
  * if ```variation group mean``` falls out of confident interval, then the difference is significant
* draw conclusion 
  * do you have a statistical significant result?
  * given the cost of lauching, is it worth to lauch it?

### Be aware besides of AB testing
* seasonality - students went on vocation
* event-drvien changes - online shopping during black Friday

### A typical AB testing interview question logic flow   
1. clarify business objective/goal (business goal) 
2. align current topic with goal
3. segment into smaller areas 
4. set up hypothesis and metric
5. validate the hypothesis by A/B testing
6. make recommendation/find root cause

### Find Root Cause:
1. sanity check: 
   1. seasonality, special events
   2. bug, issue
2. external reason: competitors
3. internal reason
   1. policy change, function change
   2. user group change
      1. some user group drops > break user group down
      2. both user group increase but overal drops > sampson's paradox, user group proportion change
                   

#### Question: Does multiple AB tests run at the same time?
Yes, in the reality, there could be hunreds of them running concurrently. Instead of let some of the feastures wait to be tested forever, we tend to ingore the correlation among those tests.
