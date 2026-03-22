---
title: "Tracking Conflict Displacement with CNNs"
image: 
  path: /assets/images/projects/tracking-conflict-displacement.jpeg
  thumbnail: /assets/images/projects/tracking-conflict-displacement.jpeg
categories: 
  - Prediction
tags:
  - neural network
  - early action
  - anticipatory action
  - conflict
  - gaza
  - palestine
  - cnn
  - tent
  - ocha
  - satellite
  - remote sensing
  
last_modified_at: 2026-03-21
---

We built a CNN to detect and count refugee tents in the Gaza Strip to quantify the humanitarian impacts of the war and better distribute aid to displaced populations.

<style>
  .responsive-video {
    position: relative;
    padding-bottom: 56.25%; /* 16:9 aspect ratio */
    height: 0;
    overflow: hidden;
    max-width: 100%;
    background: #000;
  }

  .responsive-video iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: 0;
  }

  @media screen and (max-width: 480px) {
    .responsive-video {
      padding-bottom: 75%; /* taller ratio for phones if needed */
    }
  }
</style>

# Project Overview

| **Motivation** | Ongoing conflict in Gaza has led to large-scale displacement with restricted visibility into population movements, limiting human rights violations documentation and aid delivery |
| **Model** | A CNN that can produce accurate counts of refugee tents from satellite images |
| **Client** | Forenic Architecture & United Nations Office for the Coordination of Humanitarian Affairs |
| **Status** | Complete |
| **Outcome** | Produced historic estimations of displacement from start of October 2023 conflict and live monthly estimates of displacement clusters for OCHA |



The goal was to use machine learning on satellite imagery to track the movement of displaced populations in Gaza. The work is in collaboration with Forensic Architecture and may support future court cases involving human rights violations.

![no-alignment]({{ '/assets/images/projects/motivation.jpg' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/projects/tents.png' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/updates/2025-11-november/mapping.png' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/projects/segmentation.png' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/projects/prewar1.png' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/projects/prewar2.png' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/updates/2025-july/tents-unet.jpeg' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/projects/deduplication1.png' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/projects/deduplication2.png' | absolute_url }})
*Text.*

<div class="responsive-video">
  <iframe src="https://player.vimeo.com/video/1175826790" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>
</div>
*Text.*

<div class="responsive-video">
  <iframe src="https://player.vimeo.com/video/1175826790" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>
</div>
*Text.*

![no-alignment]({{ '/assets/images/projects/tile_prediction_correlation_linear.png' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/projects/tile_prediction_correlation_log.png' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/projects/spatial_tile_error_hexbin.png' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/projects/municipal_bounds_plot.png' | absolute_url }})
*Text.*

![no-alignment]({{ '/assets/images/projects/clustering.png' | absolute_url }})
*Text.*

