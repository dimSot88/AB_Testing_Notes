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
