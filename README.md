# AB_Testing_Notes
to evaluate your test result before deciding to launch.

A naive approach (and also a response) is to launch when the lift is positive with statistical significance (p-value < alpha). Or, scrap the feature because there's no statistical significance.

An expert AB tester use, not only the lift and p-value, but also, the confidence interval to make an informed decision on the next step. 

Consider the following outcomes with the practical significance being +1.0% MDE. 

𝟭. 𝗡𝗼 𝗽𝗿𝗮𝗰𝘁𝗶𝗰𝗮𝗹 𝗮𝗻𝗱 𝘀𝘁𝗮𝘁𝗶𝘀𝘁𝗶𝗰𝗮𝗹 𝘀𝗶𝗴𝗻𝗶𝗳𝗶𝗰𝗮𝗻𝗰𝗲

The entire CI is less than the practical significance, and there's no significance since 0 is in the bound. You may want to scrap or revise the idea or re-run the experiment with increased power if your product team firmly believes that the treatment is better than the control.

Or, in some cases, maybe you don't want to see any significance given that it's a small bug fix. Then, in that case, you may just want to make the change.

𝟮. 𝗣𝗿𝗮𝗰𝘁𝗶𝗰𝗮𝗹 𝗮𝗻𝗱 𝘀𝘁𝗮𝘁𝗶𝘀𝘁𝗶𝗰𝗮𝗹 𝘀𝗶𝗴𝗻𝗶𝗳𝗶𝗰𝗮𝗻𝗰𝗲

Assuming that there's no validity threat to the experiment (meaning you've done all the sanity checks), you can proceed in ramping up or launch the change.

𝟯. 𝗡𝗲𝗴𝗮𝘁𝗶𝘃𝗲 𝗹𝗶𝗳𝘁 𝗮𝗻𝗱 𝘀𝘁𝗮𝘁𝗶𝘀𝘁𝗶𝗰𝗮𝗹 𝘀𝗶𝗴𝗻𝗶𝗳𝗶𝗰𝗮𝗻𝗰𝗲

This outcome is the exact opposite of the desired outcome. Discuss with the product team whether to scrap or revise the idea. 

𝟰. 𝗪𝗶𝗱𝗲 𝗖𝗜 𝗮𝗻𝗱 𝗻𝗼 𝘀𝘁𝗮𝘁𝗶𝘀𝘁𝗶𝗰𝗮𝗹 𝘀𝗶𝗴𝗻𝗶𝗳𝗶𝗰𝗮𝗻𝗰𝗲 

Even though there's no statistical significance, the upper bound exceeding the practical significance at +1.0% suggests that the true parameter may lie equal to or above the MDE. Re-run the experiment with increased power. If your statistical power was 80%, increase it to 90%.

𝟱. 𝗣𝗼𝘀𝗶𝘁𝗶𝘃𝗲 𝗖𝗜 𝗮𝗻𝗱 𝘀𝘁𝗮𝘁𝗶𝘀𝘁𝗶𝗰𝗮𝗹 𝘀𝗶𝗴𝗻𝗶𝗳𝗶𝗰𝗮𝗻𝗰𝗲

This is what I mean by you never just want to look at the lift and statistical significance alone. Sure, you can launch this with certain degree of confidence that your change is better than the old. However, the lower bound of the CI is lower than MDE.

To be more certain that your test brings practical significance, consider re-running with increased power.


𝟭. 𝗡𝗼𝘁 𝗮𝗹𝗹 𝘀𝗶𝗴𝗻𝗶𝗳𝗶𝗰𝗮𝗻𝗰𝗲 𝗹𝗲𝘃𝗲𝗹 (𝗮𝗹𝗽𝗵𝗮) 𝗶𝘀 𝟬.𝟬𝟱

A naive assumption in AB testing is to set the alpha as 0.05 because it's "industry practice". But, that's not always the case. 

Setting the alpha boils down to risk-reward analysis based on the type of experiment you are conducting.

As alpha == the Type 1 error rate (the probability of false rejection of Ho), you have to assess the risk of falsely rejecting the Ho and launching the test version.

If you believe that the risk is too costly in terms of business $, you can mitigate the risk by reducing alpha to 0.01.

You also need to account for multivariate testing - A/B/n, when the family-wise error rate inflates. You adjust the alpha with techniques such as Bonferroni or Sidek correction.

𝟮. 𝗢𝗯𝘀𝗲𝗿𝘃𝗮𝘁𝗶𝗼𝗻 𝘁𝗶𝗺𝗲 != 𝗘𝘅𝗽𝗲𝗿𝗶𝗺𝗲𝗻𝘁𝗮𝘁𝗶𝗼𝗻 𝗧𝗶𝗺𝗲

As an interview coach, I see that clients mistakenly believe that, if an experiment is run for 2 weeks, then a user is observed for 2 weeks. That's not the case.

Suppose you run an AB experiment for a ranking algorithm on Amazon. Your KPI is the average spend per user. You run a 14-day experiment to realize a statistical power of 80%. A user enters the experiment on day 1, then you would observe the user's total spend for 24 hours, not for the entire two weeks.

So in this case, the user observation time is 24 hours while the experimentation time to collect the required # of users (the sample size) is 2 weeks.

𝟯. 𝗗𝗼𝗻'𝘁 𝗮𝘀𝘀𝘂𝗺𝗲 𝘁𝗵𝗮𝘁 𝘆𝗼𝘂 𝘄𝗶𝗹𝗹 𝗯𝗲 𝘂𝘀𝗶𝗻𝗴 𝗧-𝗧𝗲𝘀𝘁𝘀 𝗮𝗹𝗹 𝘁𝗵𝗲 𝘁𝗶𝗺𝗲

In real-life, distributions are messy. It's not always normally distributed as assumed by T-Tests. Slight skewness is okay, as long as your sample size is large given CLT. 

But, there will be many cases when your distribution is highly skewed or inflated with zeros. Under such condition, the statistical power of the T-Tests would be reduced. 

In such cases, you may want to use more robust statistical tests such as Mann-Whitney U Test, or the zero-inflated regression model.


