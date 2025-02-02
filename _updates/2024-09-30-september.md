---
title: "2024 September"
last_modified_at: 2025-02-02
---

Technical work and some travel to Nice as flooding peaks in South Sudan.

# INFLOW Project

Continuing on with the Nile project as the flood season peaks in South Sudan. I've now built a functional temporal model and am working on perfecting the spatial model to beat a persistence model and and a constant-fill model baseline. The goal is to predict which areas of the map will be newly inundated and newly dry in each dekad. 

The spatial model task is particularly challenging since unlike the temporal model, there is no existing baseline model to compare my predictions to. In response, I have been forced to compare my predictions to default baselines like the persistence model (predict the same flooding as the previous dekad) and the constant-fill model (predict the same area of flooding as the temporal model, filling in regions that are historically more likely to be flooded first). Both of these models are quite bad and thus quite easy to beat, but this can misleadingly make my model look better than it actually is. I have been trying to avoid showing the spatial model results too much at meetings until I can better assess how well it actually performs (hopefully with a better baseline).

![no-alignment]({{ '/assets/images/updates/2024-september/rainfall.png' | absolute_url }})
*According to the TAMSAT data, this year has the highest cumulative rainfall anomaly of any year on record.*

![no-alignment]({{ '/assets/images/updates/2024-september/model-metrics.png' | absolute_url }})
*The current model is doing a good job of beating the baselines, but since the baselines are quite bad to begin with, it is challenging to to determine how useful this model would be.*

# Small Break

A quick weekend trip to Nice, France for a change of pace during this high-stress month for the Nile project (I've been working long days and sometimes nights to prep predictions for flood task force meetings). Then back to work!

![no-alignment]({{ '/assets/images/updates/2024-september/nice.png' | absolute_url }})
*Nice.*

![no-alignment]({{ '/assets/images/updates/2024-september/church.png' | absolute_url }})
*Pro tip: Eglise Saint-Jacques-le-Majeur has a secret bar in the back, accessed through a secret entrance.*

![no-alignment]({{ '/assets/images/updates/2024-september/room.png' | absolute_url }})
*Finally settled and finished decorating our new room.*