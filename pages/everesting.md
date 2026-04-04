---
layout: default
---

## Using ML to Tackle a Cycling Challenge
**Images coming at a future date**

### Overview
"Everesting" is a cycling challenge that "rose to prominence" (a little mountain-based humor) during the pandemic, and entails repeatedly riding a trail until your overall elevation gain equals that of Everest above sea level (8848 m). As an undergraduate student, I had the opportunity to volunteer on a research project that involved scraping publicly available data and using machine learning to find if there is a best way to approach this challenge based on your relative experience as a cyclist. 

My own involvement was limited to the data collection, validation, and exploratory analysis stages for this project, with results ultimately fed to gaussian mixture models for the final pubication. I received an acknowledgment for my troubles.

### Data Collection
I scraped data from everesting.cc and veloviewer using a combination of methods. The first was used on everesting.cc and involved digging through the site using Chrome's developer tools until I found a json file that contained all of the site's data. A handy Python script developed with a little data sleuthing converted this json file into something usable for our purposes, including a list of veloview links for the hills actually used for this challenge. This was then fed into webscraper.io, a Chrome plugin, and the remaining data of interest was made available from there. 

### My Preliminary Analysis
With data in hand and fully anonymized, the real challenge began: assessing which subset of the data was actually meaningful for this study. After all, the most useful data would consist of completed attempts on a physical bike that obeyed the rules of the challenge. The study also chose to only look at attempts from athletes 16+ years of age.  

The rules of the competition:
1. It must be a continuous attempt
2. Total elevation gain (counting only the uphill) needs to meet or exceed that of Everest.

On the first rule, as well as the criteria of physical bike rides, I eliminated virtual rides as well as rides longer than 2 days in duration from further consideration. This 2-day cutoff, in addition to making sense from a sleep deprivation standpoint, was also supported when looking at a histogram of elapsed times. Additionally, based on the nature of the challenge, if a rider reported zero hill repeats then their data was also likewise excluded.

In the spirit of also eliminating spurious data points at this stage, I took a look at the distribution of speeds for the remaining attempts. I found a cutoff of 40 km/h was reasonable based on the data as well as considering the physical exertion required to maintain higher speeds and likelihood of obtaining them on a bicycle. Most amusing was the extreme outlier that self-reported an average speed of mach 13. Truly an incredible specimen. 

Checking elevation gain was more interesting, as it involved catching discrepancies between the claimed elevation gain and the available Strava data about the gradient of the hill and length of the trail. Using a little trigonometry and idealizing each segment as a right triangle with angle of elevation proportional to the reported average grade, I was able to compute how much elevation they should have gained. Looking once again at distributions, I was able to see that 10% deviation from the elevation of everest was an acceptable cutoff for excluding attempts where the numbers almost literally did not add up. 

Now armed with a full dataset, I did a little digging around to see if there were any visually obviously meaningful associations between the possible explanatory variables for cyclist performance in this challenge. After playing around a little, I found that gradient and distance had a meaningful relationship. This made sense, because there's a natural tradeoff there. 

The principal investigator took it from there, and deployed the gaussian mixture models as well as other forms of analysis to yield the conclusions outlined in their report. 

### Published in
[Nature Scientific Reports](https://www.nature.com/articles/s41598-023-29435-w)


[Return Home](../index.html)
