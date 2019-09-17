# AB_Testing_Notebook
AB testing for beginners

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
