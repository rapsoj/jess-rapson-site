---
title: "2025 September"
last_modified_at: 2025-10-05
---

*Perfectionism will kill your progress. If you're afraid to start because you think you'll fail that's the sign you have to do it right there right now.*

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
  }
</style>

# Algorithmic Governance Foundation CIC

Got the AGF incorporated as a CIC (community interest company, essentially a legal status in the United Kingdom for non-profit entities). This unlocks a ton of new avenues for grant applications, contracts, and collaborations. 

This initiative has come a long way since I first conceived of starting it last year. We now have 30 active student/early career volunteers from 9 different countries, working on projects with 8 different orgs (including major government departments). The AGF is also part of the UN’s AI for Good initiative (as I'm a leader of the Oxford Hub).

For me, starting something that necessitates getting other people involved and supportive is extremely hard. I am naturally a very independent person (and a bit of a perfectionist), so would much rather keep my ideas to myself and only show off the end result once it's finished and flawless. It is a huge leap of faith getting people involved and excited in the early stages, and my hesitation on this point is probably why it's taken me so long to get to this level. Going forward, I imagine this is going to be less and less of a barrier, as doing it once demystifies the process substantially.

Please check out [the AGF website](https://algorithmicgovernance.org/) to keep an eye on the projects we're working on, request specific projects for your org, or get involved.

# Wrapping Up Projects

The overarching theme of this month for me was winding down AGF projects to prepare for focussing on my DPhil. The way I want to run this, for now, is to ramp up the student projects over the holidays (winter break, spring break, summer break) and focus on my research and project acquisition/promoting the work from completed projects in the interim.

I've completely finished the electronic vulnerabilities and capabilities assessment (eVCA) tool for the Red Cross (deployed on HuggingFace), my conflict forecasting team has completed the big scrape for augmenting the ACLED conflict data to better predict global conflict, my AMR tracking team has completed and deployed a LLM/web-scraping tool to compare specific policies around the world (with specific applications for identifying gaps in the vaccine approval process in ASEAN countries; also deployed on HuggingFace), and completed a model to predict water quality parameters remotely for the Fish Welfare Institute.

<div class="responsive-video">
  <iframe src="https://player.vimeo.com/video/1124630429" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>
</div>
*The electronic vulnerabilities and capabilities assessment (eVCA) allows the Red Cross team to quickly identify exactly which communities are affected by a wide selection of hazards – with the option of adding more analysis on intersecting hazards and assets.*

![no-alignment]({{ '/assets/images/updates/2025-09-september/deep-resevoir.png' | absolute_url }})
*Our tool for instantly comparing and set of policies (at any detail level) across jurisdictions.*

We've also made incredibly good progress on our displacement/tent detection model for the Gaza Strip. After doing a bit of a literature review, it was immediately clear that feeding the model an image of the same area from the pre-war period makes it much easier for the U-net to learn which parts of the current image are tents. This makes intuitive sense, and you can see in the below image how these areas pop up as clear red blobs when they are differenced.

![no-alignment]({{ '/assets/images/updates/2025-09-september/gaza-prewar.png' | absolute_url }})
*Since the tents don't exist in the pre-war image, it's easier for the model to distinguish them from similar looking white buildings and structures.*

Though it is unlikely to influence the current state of affairs in the Gaza Strip, this work is incredibly important for helping to document atrocities and war crimes committed, as well as getting an accurate estimate of the human impact of the war. Though our work is fundamentally technical (making it sometimes difficult to connect with actual human suffering), we are easily reminded of the scale of destruction while going through the satellite data. Near the end of last month, there was an entire displacement camp that was targeted by Israeli bombing (see the photo below). With data from our model, atrocities such as these can be documented and quantified, hopefully providing a legal path to prevent or discourage such acts in the future.

![no-alignment]({{ '/assets/images/updates/2025-09-september/gaza.jpg' | absolute_url }})
*The entire neighbourhood was completely destroyed on August 25th, forcing the displaced populations to flee yet again.*

Wrapping these up has not given me any more free time. The budding success of the AGF projects ran this summer have already spilled into substantive follow-up presentations and additional project requests. Several groups have reached out to learn more about the ACLED CAST model improvements we have achieved, including Global Affairs Canada, the Canadian Department of Defence, and the Red Cross Climate Centre. The UK's Medicines and Healthcare products Regulatory Agency (MHRA) is also in the process of contracting with us to build on our LLM/web-scraping policy tracker. And I've started a technical paper on reducing bias in predictive policing algorithms for the London Metropolitan Police Service (in response to a [government posting](https://www.gov.uk/government/news/ai-to-help-police-catch-criminals-before-they-strike) on an upcoming AI-based crime map). 

![no-alignment]({{ '/assets/images/updates/2025-09-september/un-cities.png' | absolute_url }})
*Also sitting on some UN expert groups for AI, though still quite skeptical that these will amount to anything useful.*

The ultimate goal for the AGF (in my mind) is to be able to implement algorithmic solutions in highly impactful government bodies; and it seems the way to do this is to do smaller projects for public serving groups (like non-profits and think tanks) until the work is noticed by these government bodies. 

I'm at the point for the AGF where the projects are impactful, the clients are in good supply, and the student researchers are extremely competent. What I am desperately missing, however, is a co-director to help me manage client relations and impact. This will be my focus for next month, and is key to scaling.

# Starting the DPhil

Outside of work, I'm prepping to start my DPhil. After a bit of an uphill battle, I've managed to secure partial funding for the first year of my DPhil, but still to find something  to cover living costs.

![no-alignment]({{ '/assets/images/updates/2025-09-september/bod-card.png' | absolute_url }})
*I'm back.*

# Life

In non-work events: I made some pink jam from invasive [Himalayan Balsam](https://en.wikipedia.org/wiki/Impatiens_glandulifera) which has taken over the Thames in Oxford, caught a double rainbow from the office, went to a secret forest party, and helped clean the flat living room to be cozy for the fall.

![no-alignment]({{ '/assets/images/updates/2025-09-september/jam.png' | absolute_url }})
*Himalayan Balsam petles, before becoming jam.*

<div class="responsive-video">
  <iframe src="https://player.vimeo.com/video/1124630440" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>
</div>
*It's legally jam.*

![no-alignment]({{ '/assets/images/updates/2025-09-september/rainbow.jpeg' | absolute_url }})
*Double rainbow!*

<div class="responsive-video">
  <iframe src="https://player.vimeo.com/video/1124630447" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>
</div>
*Secret forest party.*

![no-alignment]({{ '/assets/images/updates/2025-09-september/living-room.png' | absolute_url }})
*It's at least clean until Alec comes home.*

![no-alignment]({{ '/assets/images/updates/2025-09-september/road.jpeg' | absolute_url }})
*Saying goodbye to summer by Folly Bridge.*
