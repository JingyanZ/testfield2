# A/B Test Design
<!--
.. title: AB TEST DESIGN
.. slug: ab-test-design
.. tags: statics, ab-test
.. category: Statistics Report
.. guid: 04
.. description: AB Test Design of the Udacity Project 
.. date: 2017-11-14 10:30:00 UTC+08:00
.. base_url: http://www.testfield.cc/
.. type: text
-->


### Background of the Project

> At the time of this experiment, Udacity courses currently have two options on the course overview page: "start free trial", and "access course materials". If the student clicks "start free trial", they will be asked to enter their credit card information, and then they will be enrolled in a free trial for the paid version of the course. After 14 days, they will automatically be charged unless they cancel first. If the student clicks "access course materials", they will be able to view the videos and take the quizzes for free, but they will not receive coaching support or a verified certificate, and they will not submit their final project for feedback.  
> In the experiment, Udacity tested a change where if the student clicked "start free trial", they were asked how much time they had available to devote to the course. If the student indicated 5 or more hours per week, they would be taken through the checkout process as usual. If they indicated fewer than 5 hours per week, a message would appear indicating that Udacity courses usually require a greater time commitment for successful completion, and suggesting that the student might like to access the course materials for free. At this point, the student would have the option to continue enrolling in the free trial, or access the course materials for free instead. This screenshot shows what the experiment looks like.  
> The hypothesis was that this might set clearer expectations for students upfront, thus reducing the number of frustrated students who left the free trial because they didn't have enough time—without significantly reducing the number of students to continue past the free trial and eventually complete the course. If this hypothesis held true, Udacity could improve the overall student experience and improve coaches' capacity to support students who are likely to complete the course.  
> The unit of diversion is a cookie, although if the student enrolls in the free trial, they are tracked by user-id from that point forward. The same user-id cannot enroll in the free trial twice. For users that do not enroll, their user-id is not tracked in the experiment, even if they were signed in when they visited the course overview page.  
>Cited from Udacity

### Metric Choice
#### Invariant Metric
1. Number of Cookies: That is, number of unique cookies to view the course overview page.

Reason: “In the experiment, Udacity tested a change where if the student clicked ‘start free trial’, they were asked how much time they had available to devote to the course.” Data of number of cookies to view the course overview page is before the change.  Therefore, number of cookies should not be influenced by the experiment. It should be an invariant metric.

2. Number of Clicks: That is, number of unique cookies to click the "Start free trial" button (which happens before the free trial screener is trigger). 

Reason: The behavior of clicking the "Start free trial" button is before the checking out process which is the experiment. Therefore number of clicks should not influenced by the experiment. It should be an invariant metric.


3. Click Through Probability: That is, number of unique cookies to click the "Start free trial" button divided by number of unique cookies to view the course overview page. 

Reason: Both number of unique cookies to click the "Start free trial" button and number of unique cookies to view the course overview page are invariant metrics. Therefore click through probability which is unique cookies to click the "Start free trial" button divided by number of unique cookies to view the course overview page is an invariance metric.

#### Evaluation Metric
1. Gross Conversion: That is, number of user-ids to complete checkout and enroll in the free trial divided by number of unique cookies to click the "Start free trial" button. 

Reason: Gross conversion are number of user-ids to complete checkout and enroll in the free trial divided by number of unique cookies to click the "Start free trial" button.  In the experiment,  users will be asked an question of validate study time, and who choose the option “fewer than 5 hours per week” will be given another suggestion to access to “course materials for free”.  It will make an influence on number of user-ids enrolling in the free trial by setting clearer expectations for students upfront, thus reducing the number of frustrated students who left the free trial because they didn't have enough time, which is the hypothesis of the experiment. Addition ,  number of unique cookies to click the "Start free trial" button are invariant metric and the unit of diversion is a cookie. Therefore,  gross conversion is chosen as an evaluation metric.

2. Net Conversion: That is, number of user-ids to remain enrolled past the 14-day boundary (and thus make at least one payment) divided by the number of unique cookies to click the "Start free trial" button.

Reason: Number of user-ids who enroll in the free trial will be influenced by the checkout process in the experiment.  Remaining enrolled and making at least one payment is the process after enrolling in the free trial. Therefore, number of user-ids could be influenced by the experiment. Gathering data of number of user-ids to remain enrolled will help to test the hypothesis that  “without significantly reducing the number of students to continue past the free trial”.  Addition , number of unique cookies to click the "Start free trial" button is invariant metric and the unit of diversion is a cookie . Therefore, net conversion is chosen as an evaluation metric.

#### Metric which are not  chosen as evaluation or invariant metric.

1. Number of user-ids: That is, number of users who enroll in the free trial.

Reason: Number of user-ids will be affected by the experiment. However, the difference between number of user-ids in the control group and the experiment group may be caused by experiment or data gathering.  Therefore, using conversion is a better way to make comparison between  the control group and the experiment group.

2. Retention: That is, number of user-ids to remain enrolled past the 14-day boundary (and thus make at least one payment) divided by number of user-ids to complete checkout. 

Reason:  After sample size calculation, more than 100 thousand pageviews will be needed, which can be hardly gathering in the experiment. Therefore retention will not be used in the experiment.

The hypothesis of the experiment is that set clearer expectations for students upfront, thus reducing the number of frustrated students who left the free trial because they didn't have enough time—without significantly reducing the number of students to continue past the free trial and eventually complete the course.  Therefore, the result that is expected is that gross conversion is significantly changed in the experiment group. The net conversion is not significantly changed in the experiment  at the same time.

### Measuring Standard Deviation
Standard Deviation of  Gross Conversion: 0.0202

Standard Deviation of Net Conversion: 0.0156

Because in both gross conversion and net conversion the unit of analysis  are cookies. And the unit of diversion. The unit of diversion and unit of analysis are match. Therefor, there is no need to calculate empirical variability.

### Sizing

Not using Bonferroni correction.
Pageviews: 685325

### Duration vs. Exposure

Fraction of Traffic Expose: 0.62
Length of Experiment: 28 days

Considering seasoning factor which is unique cookies to view course overview page  may have difference between weekday and weekends. Therefore 28days (4 weeks)  is chosen  as the length of the experiment. Although more than half of the traffic will be in the experiment. In order not to expand the experiment too long, the  fraction of 0.62 are chosen.

Students in the experiment would not take risks also for four reasons below:
1. Students are allowed to access to the free trial even their study time is less than 5 hours per week.
2. Process of enrollment or taking free material are almost the same in the experiment, only a checkout will be added. Student would not have to spent much time to get adapted to the checkout in the experiment.
3. The experiment would not change the database.
4. Students’ private information would not be gathering during the checkout.

## Experiment Analysis
### Sanity Checks

Number of Cookies
95% CI = （0.4988， 0.5011）
Observed Value: 0.5006
Pass the sanity check.

Number of Clicks
95% CI = (0.4958, 0.5041)
Observed Value: 0.5004
Pass the sanity check.

Click Through Probability
95% CI = (-0.0012, 0.0013)
Observed Value: 0.000
Pass the sanity check.

## Result Analysis
### Effect Size Tests
#### Gross Conversion

Null hypothesis (Ho):  
Number of user-ids who enroll in the free trial is not changed by the experiment. And gross conversion in the control group and the experiment group are almost the same  (d=0).

Alternative Hypothesis (HA): 
 Number of user-ids who enroll in the free trial is significantly changed by the experiment. And gross conversion in the control group and the experiment group are significantly different and not by chance  (d≠0). 

two trail test
α = 0.05

SEpool = 0.0034
d^ = -0.0049
dmin= 0.01
95% CI = (-0.0291, -0.012)

Result: reject Ho
Number of user-ids who enroll in the free trial is significantly changed by the experiment. Gross conversion in experiment group is statistical significant and practically significant changed compared to control group. 

#### Net Conversion

Null hypothesis (Ho):  
 Number of user-ids to remain enrolled past the 14-day boundary is significantly changed in the experiment. Net conversion in the control group and the experiment group are significantly different and not by chance  (d≠0).

Alternative Hypothesis (HA):  
 Number of user-ids to remain enrolled past the 14-day boundary is not changed in the experiment. And net conversion in the control group and the experiment group are almost the same  (d=0).

two trail test
α = 0.05

SEpool = 0.0034
d^ = -0.0049
dmin = 0.0075
95% CI = (-0.0116, 0.0019)

Result: reject Ho
Net conversion in experiment group is neither statistical significant nor practical significant changed compared to control group.  

### Sign Tests
#### Gross Conversion

Null hypothesis (Ho):  
Number of user-ids who enroll in the free trial is not changed by the experiment. And gross conversion in the control group and the experiment group are almost the same.

Alternative Hypothesis (HA): 
 Number of user-ids who enroll in the free trial is significantly changed by the experiment. And gross conversion in the control group and the experiment group are significantly different and not by chance. 

two trail test
α = 0.05

P value =  0.0026


Result: Reject Ho
Number of user-ids who enroll in the free trial is significantly changed by the experiment. Gross conversion in experiment group is statistical significant changed compared to control group. 

#### Net Conversion
Null hypothesis (Ho):  
 Number of user-ids to remain enrolled past the 14-day boundary is significantly changed in the experiment. Net conversion in the control group and the experiment group are significantly different and not by chance.

Alternative Hypothesis (HA):  
 Number of user-ids to remain enrolled past the 14-day boundary is not changed in the experiment. And net conversion in the control group and the experiment group are almost the same.

two trail test
α = 0.05

P value =  0.6776

Result: Reject Ho
 Number of user-ids to remain enrolled past the 14-day boundary is not significantly changed in the experiment. Net conversion in experiment group is not statistical significant changed compared to control group.  

## Summary
 Bonferroni correction is not used in the analysis.

In order to use Bonferroni correction, αoverall has be to calculated, which is assuming that metrics are independent. However in the experiment metric are related and will move together.  Bonferroni correction is way much conservative for the experiment.

## Recommendation
I will not launch the experiment. Even thought the gross conversion is significantly improved in the experiment, the confidence interval of net conversion are between -0.0116 and 0.0019,. The experiment may cause the decrease of net conversion. The P value of net conversion is 0.6676,  the net conversion could practically significantly decrease to some degree.

## Follow-Up Experiment
Student cancellation early in the course is caused by a variety of reasons, like lacking of study time, or not meet the knowledge requirements for taking the course. The experiment I will try is that when students clicked "start free trial” button, they will be asked to take a test about the required knowledge for taking this course.  By evaluating the scores of the test, it will give student suggestion if they need take other courses to meet the requirement.

My hypothesis would be this experiment will reduce the student who left the free trial because they didn’t meet the knowledge requirement of the course without significantly reducing the number of students to continue past the free trial.

The unit of diversion is a cookie.

 Metric:
1. Number of Cookies: That is, number of unique cookies to view the course overview page.

Reason: Invariant metric, for sanity check.

2. Number of Clicks: That is, number of unique cookies to click the "Start free trial" button.

Reason: Invariant metric, for sanity check.

3. Click Through Probability: That is, number of unique cookies to click the "Start free trial" button divided by number of unique cookies to view the course overview page. 

Reason: Invariant metric, for sanity check.

4.  Gross Conversion: That is, number of user-ids to complete test and enroll in the free trial divided by number of unique cookies to click the "Start free trial" button. 
Reason: Evaluation metric, to evaluate whether test will effect students choice to enroll in the free trial.

5. Net Conversion: That is, number of user-ids to remain enrolled past the 14-day boundary (and thus make at least one payment) divided by the number of unique cookies to click the "Start free trial" button.

Reason: Evaluation metric, to evaluate whether test will effect number of students to remain enrolled past the 14-day boundary.





 
