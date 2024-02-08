---
title: "Increasing the Efficacy of the G7 and G20 Using Predictive AI"
image: 
  path: /assets/images/projects/g7-g20-commitments/cover.jpeg
  thumbnail: /assets/images/projects/g7-g20-commitments/cover.jpeg
categories:
  - Prediction
tags:
  - development
  - economy
  - international cooperation
  - g7
  - g20
  - international governance
  - international
  - canada
  - united states
  - france
  - european union
  - eu
  - united kingdom
  - uk
  - us
  - usa
  - germany
  - italy
  - japan
last_modified_at: 2024-02-08
---

Data collected by the G7 and G20 Research Groups has made it possible to produce data-driven estimates of the probability that each member nation will meet their summit commitments. I developed this predictive model to enable Sherpas to better allocate resources towards at-risk commitments, thus making the G7 and G20 more effective.

# Project Overview

| **Motivation** |  Fewer than two thirds of commitments made by leaders at past G7 and G20 summits have been met in full |
| **Model** | An interactive machine learning-based tool that predicts the probability that each member nation will meet a given summit commitment |
| **Client** | G7 and G20 Research Groups |
| **Status** | Complete |
| **Outcome** | Shared results with G20 Sherpas and presented work at the G20 Delhi Summit |

During its almost 50-year existence, [the G7 has served as an international forum](https://en.wikipedia.org/wiki/G7) for promoting the liberal and democratic ideals championed by its members. To this effect, the organization has collectively made over six thousand commitments to tackle issues such as global development, climate change, health policy and financial regulation. Historically, however, only 62&#37; of these commitments have been met in full. For the G7 to succeed in its mission, it is critically important that member nations comply with the commitments that they themselves make.

# What is the tool?

[Past research](https://www.globalgovernanceproject.org/increasing-the-impact-of-the-g7-2/) has shown that the underlying factors behind whether G7 member nations will comply with commitments primarily relate to immutable properties such as the economic position of the country or past compliance with similar commitments. These factors cannot be leveraged to improve the probability of compliance as they cannot be changed. However, by building a model to predict compliance, it becomes possible to identify which member nations are the least likely to meet their G7 commitments – enabling resources to be leveraged to assist the member nation in fulfilling their obligations. This could improve the overall efficacy of the G7. 

![no-alignment]({{ '/assets/images/projects/g7-g20-commitments/tool1.png' | absolute_url }})

The [G7 Compliance Simulator](https://g7-utoronto.shinyapps.io/compliance-tool/) seeks to do exactly this. Interested parties can access the tool online and enter relevant information to identify which member nations may need assistance in meeting their G7 obligations.

![no-alignment]({{ '/assets/images/projects/g7-g20-commitments/tool2.png' | absolute_url }})

# How does it work?

Using each G7 members’ historic performance on 655 individual commitments (a total of 5,994 individual assessments) the impact of various summit and commitment characteristics were fitted to a binomial regression model.

This revealed that several key characteristics of summits and commitments, such as references to democracy or human rights, holding ministerial meetings before G7 summits, forming official G7 bodies in the relevant issue-area, and hosting the summit were associated with a significant increase in the probability of a given member nation complying with a specific G7 commitment.

![no-alignment]({{ '/assets/images/projects/g7-g20-commitments/summit.png' | absolute_url }})

Similarly, the summit host country appeared to influence levels of compliance. Compliance levels were higher when the United Kingdom hosted the G7 summit and lower when France and Canada hosted.

![no-alignment]({{ '/assets/images/projects/g7-g20-commitments/host.png' | absolute_url }})

There was also variation in the probability of compliance between G7 members. The European Union and United Kingdom were more likely to fulfill commitments, while France, Japan, and Italy were less likely to do so.

![no-alignment]({{ '/assets/images/projects/g7-g20-commitments/member.png' | absolute_url }})

Finally, compliance probability varied by the commitment’s area of focus. Compliance was more likely for commitments regarding social policy, international cooperation, information and communications technology (ICT) and digitization, labour and employment, and energy. Commitments were less likely to be achieved for commitments regarding education and gender.

![no-alignment]({{ '/assets/images/projects/g7-g20-commitments/issue.png' | absolute_url }})

# What are the caveats of this approach? 

Despite the many significant variables that were found, the overall explanatory power of the model is very low. Even when all summit characteristics, member nation properties, and commitment features are considered together, only 7.3&#37; of the variance in G7 compliance could be explained (McFadden’s pseudo R2). This suggests that the majority of G7 compliance may be determined by unknown factors or may be simply random.

Nonetheless, there is hope for increasing G7 effectiveness. All the significant variables examined can be combined into a model to predict future compliance. The binomial logistic regression model can predict compliance in a holdout set with 67&#37; accuracy, while a random forest classifier model trained on the same data is able to predict compliance with 70&#37; accuracy. Though not perfect, this second model performs much better than chance, enabling potential compliance issues to be detected with the simulation tool as soon as commitments are made so that resources can be directed accordingly. 

Increasing G7 effectiveness by leveraging patterns associated with higher probabilities of compliance is extremely difficult, as most performance is likely determined by factors outside the control of the organization. However, by using available data to predict future compliance, it may be possible to direct resources to assist member nations at higher risk of failing to meet their obligations — thus improving the overall ability of the G7 to achieve its goals.

*All data and code for this analysis can be found [here](https://github.com/rapsoj/g7-compliance).*

*The G7 Compliance Simulator can be accessed [here](https://g7-utoronto.shinyapps.io/compliance-tool/).*