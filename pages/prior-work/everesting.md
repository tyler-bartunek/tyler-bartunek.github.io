---
layout: default
---

## Using ML to Tackle a Cycling Challenge

<figure style="text-align: center;">
<img src="{{ '/assets/img/everesting/everest_abstract.png' | relative_url}}" alt="Visual Abstract" style="width: 100%;">
<figcaption style="font-size: 0.85em; color: #666;">Webscraping and data analysis yield insights into a popular cycling challenge. Photo by <a href="https://unsplash.com/@segerfredo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Frederik Rosar</a> on <a href="https://unsplash.com/photos/a-person-riding-a-bike-on-a-mountain-F_sGPBDM1FI?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>.</figcaption>
</figure>

### Overview
"Everesting" is a cycling challenge that rose to "prominence" (a little mountain-based humor) during the pandemic, and entails repeatedly riding a trail until your overall elevation gain equals that of Everest above sea level (8848 m). As an undergraduate student, I had the opportunity to volunteer on a research project that involved scraping publicly available data and using machine learning to find if there is a best way to approach this challenge based on your relative experience as a cyclist. 

My own involvement was limited to the data collection, validation, and exploratory analysis stages for this project, with results ultimately fed to gaussian mixture models for the final publication. I received an acknowledgment in the a _Nature Scientific Reports_ article for my troubles.

### Data Collection
I scraped data from everesting.cc and veloviewer using a combination of methods. The first was used on everesting.cc and involved digging through the site using Chrome's developer tools until I found a json file that contained all the site's data. A handy Python script developed with a little data sleuthing converted this json file into something usable for our purposes, including a list of veloview links for the hills actually used for this challenge. This was then fed into webscraper.io, a Chrome plugin, and the remaining data of interest was made available from there. 

### My Preliminary Analysis
With data in hand and fully anonymized, the real challenge of assessing which subset of the data was meaningful for this study began. After all, the most useful data would consist of completed attempts on a physical bike that obeyed the rules of the challenge. The study also chose to only look at attempts from athletes 16+ years of age out of caution/skepticism that athletes younger than this were actually completing this rigorous of a challenge.  

The rules of the competition:
1. It must be a continuous attempt
2. Total elevation gain (counting only the uphill) needs to meet or exceed that of Everest.

On the first rule, as well as the criteria of physical bike rides, I eliminated virtual rides as well as rides longer than 2 days in duration from further consideration. This 2-day cutoff, in addition to making sense from a sleep deprivation standpoint, was also supported when looking at a histogram of elapsed times. Additionally, based on the nature of the challenge, if a rider reported zero hill repetitions then their data was also likewise excluded.

<div style="text-align: center;">
<img src="{{ '/assets/img/everesting/everest_speed_time_plots.png' | relative_url}}" alt="Data plots" style="width: 100%;">
</div>

In the spirit of further eliminating data of dubious integrity, I looked at the distribution of speeds for the remaining attempts. I found a cutoff of 20 mph was reasonable based on the data as well as considering the physical exertion required to both obtain and maintain higher speeds than this on a bicycle. Most amusing was the extreme outlier I found that self-reported an _**average**_ speed of Mach 13. Truly an incredible specimen. 

Checking elevation gain was more interesting, as it involved catching discrepancies between the claimed elevation gain and the available Strava data about the gradient of the hill and length of the trail segment. Using a little trigonometry and idealizing each segment as a right triangle with angle of elevation proportional to the reported average grade, I was able to compute how much elevation they should have gained. Looking once again at distributions, I was able to see that 10% deviation from the elevation of everest was an acceptable cutoff for excluding attempts where the numbers almost literally did not add up. Please ignore the figure title, the "k" and "removed" are errors.

<div style="text-align: center;">
<img src="{{ '/assets/img/everesting/everest_elevation_err_plot.png' | relative_url}}" alt="Data plots" style="width: 100%;">
</div>

Now armed with a full dataset, I did a little digging around to see if there were any obviously meaningful associations (from a visual perspective) between the possible explanatory variables for cyclist performance in this challenge. After playing around a little, I found that gradient and distance had a meaningful relationship. This made sense to me, because there's a natural tradeoff there. 

<div style="text-align: center;">
<img src="{{ '/assets/img/everesting/everest_dist_grad_plot.png' | relative_url}}" alt="Gradient v Distance" style="width: 75%;">
</div>

The principal investigator took it from there, and deployed the gaussian mixture models as well as other forms of analysis to yield the conclusions outlined in their report. 

### Published in
[Nature Scientific Reports](https://www.nature.com/articles/s41598-023-29435-w)
