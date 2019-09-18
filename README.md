# AB_Testing_Notebook

### What is AB testing?
In a word, ab testing is an experiment that randomly split your users into 2 or multiple groups, and test whether your product new feature could hit a better performance. Users view original product/page are called "Control group", and users view new features are called "Variation Group". Generally, you don't want too many variations for a single test, because the more variations created, the higher possibility it could fall out of confidence interval.

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
  *  generally single metric is eaiser to evaluate and avoid chaos
  *  if you have multiple metrics need to be evaluate, try to make it as a composite metric such as OEC(overall evaluation criterion). But the tricky part is how to set the weights of different metrics to this composite metric.

* Additional resource to collect data?
  *  user experience research: could only focus on small group of users, data are deep but less
  *  focused group: target a specific group of people, present to them and hear feedbacks. The issue is that you may hear less vocie than you expect, 1-2 loud voice could also affect others thoughts
  *  survey: you could collect a lot of data in this way, but what people said may differ from what they truly thought
  
### Common Metrics
* Engagement
  *  Count: DAU (daily active user),MAU (monthly active user) - how do you define active?
     * if the activity has significant weekly deffirence, consider MAU as 28 daya instead of 30 days
  *  Mean : average time spent
  *  Ratio: DAU/MAU ratio - truly engagement rate
* Revenue
  *  Mean : average $ spent per user
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

#### Binomial Distribution: (for probablity)
 * estimated probablity (p hat) = # users who click / # users who view page 
  * standard error = sqrt(p hat * (1 -p hat) / # users who view page)
 *  sanity check: if p hat * # users who view page  > 5 and (1 - p hat)* # users who view page  > 5, we can use normal distribution to find margin of error
 * margin of error = z score * standard error
 * upper bound = p hat + margin of error
 * lower bound = p hat - margin of error
