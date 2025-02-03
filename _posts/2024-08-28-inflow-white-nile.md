---
title: "Improving Flood Prediction Along the White Nile with Neural Networks"
image: 
  path: /assets/images/projects/inflow-white-nile.jpeg
  thumbnail: /assets/images/projects/inflow-white-nile.jpeg
categories: 
  - Prediction
tags:
  - neural network
  - early action
  - anticipatory action
  - flooding
  - south sudan
  - white nile
  - nile
  - spatio-temoral
  - forecasting
  
last_modified_at: 2025-02-02
---

I built a two-stage neural network to automatically predict extreme out-of-sample inundation extent in the White Nile basin in South Sudan using satellite data from open sources.

# Project Overview

| **Motivation** | Flooding in the White Nile basin in South Sudan is difficult to predict due to the risk of future flood events exceeding past records, impairing the timely and effective distribution of humanitarian aid |
| **Model** | A two-stage neural network producing temporal and spatial predictions of inundation in South Sudan |
| **Client** | University of Reading |
| **Status** | Complete |
| **Outcome** | Produced live predictions of flooding during the 2024 flood season, presented work to UNHCR, deployed model to be put on JASMIN |

![no-alignment]({{ '/assets/images/updates/2024-july/nile-flooding.png' | absolute_url }})

*Currently, the Sudd basin is flooded much more than normal in a way that no model was able to predict. The challenge was to build a model that can predict these kinds of extreme events without any equivalent samples in the training data.*

The primary challenge of the data is that the issue being modelled (extreme flooding events) may not have occurred yet. While the Sudd basin has been inundated beyond normal levels for several years, the current flood situation is unprecedented and was not predicted by any existing models. So the question at hand is: if a similarly unprecedented situation were to occur several years from now, could the model predict it?

![no-alignment]({{ '/assets/images/updates/2024-july/percent-inundated.png' | absolute_url }})
*The prediction challenge is that while some areas of the basin are always inundated, there are a very small portion of crucial areas (mainly refugee camps and other human settlements) that are flooded, but only very rarely.*

![no-alignment]({{ '/assets/images/updates/2024-july/rare-inundation.png' | absolute_url }})
*A model that can predict when these areas will be inundated would be instrumental in allocating aid. In addition, aid agencies are interested in knowing when/why the current high levels of flooding will dissipate.*

The project involved testing a large number of potential solutions and further develop the best performing method. These include:

1. Hierarchical models, where one model is trained on non-extreme data, one on extremely low data (drought), and one on extremely high data (flood); an additional model is used to determine which model should be used to issue the prediction, as proposed by Li, Xu, and Anastasiu (2023) in *An Extreme-Adaptive Time Series Prediction Model Based on Probability-Enhanced LSTM Neural Networks*

2. Quantile neural networks, where pinball loss is used during training to natively produce estimates of different quantiles, providing a better understanding of uncertainty

3. Linear-based gradient constraints, where the gradient descent process is restricting such that the neural network forms near-linear associations between variables (this helps with overfitting, but may render the complexity-modelling benefits of neural networks moot)

4. Extreme value loss, where the loss function is set to punish inaccuracies on extreme values substantially more than equivalent inaccuracies on average values

5. Multi-model ensembles, where the outputs of neural networks are combined with other models like tree-based methods or quantile regression, which may be more capable of extracting relationships beyond those present in the training data

Testing extreme values was done by excluding the current flooding situation completely from the training data and testing to see which models are best at predicting it. 
