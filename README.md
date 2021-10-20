## Bird Data Summary

This readme summarizes a consolidated dataset of ~10K bird species that includes diet information, size, habitat, threatened status, nature of threat, and other bird characteristics.


## Business Problem

In September 2021, the Ivory-billed Woodpecker was declared extinct. Eight species of birds in Hawaii are expected to share a similar fate due to habitat removal and the presence of invasive species. The World Ornithological Society (WOS) has an interest in the conservation of bird species of the world. To best direct research funding and target conservation efforts the WOS has asked us to build a predictive model to accurately identify threatened bird species.
<br />  
We aim to use Machine Learning techniques to construct a predictive model trained on current threatened status. Our data includes diet, strategies of foraging/hunting, biological features of the bird(s), types of environmental threats, habitats, and breeding location.  
<br />
Developing a model to predict threatened status, we can identify factors that most contribute to species decline. The WOS can utilize the model to strategically plan conservation efforts and prioritize research funding. 
<br />  
We may want to pay special attention in situations where our model produces false positives (the model thinks that a species is threatened, when in fact it's not). These birds, while not currently threatened, have characteristics of threatened birds and are worthy of research into what strategies have made their species successful.

## Sources

Diet:
* Paper: https://figshare.com/collections/EltonTraits_1_0_Species-level_foraging_attributes_of_the_world_s_birds_and_mammals/3306933
* Github: https://github.com/hurlbertlab/dietdatabase  

Other bird features:
* Data Dictionary: http://datazone.birdlife.org/species/spcrange
* Data Query Portal: http://datazone.birdlife.org/species/search
* Main Website: https://www.birdlife.org  

Red List (threatened, endangered, etc):
* https://www.iucnredlist.org


## Notebooks
* threats_habitats_merge.ipynb: pulls habitat, threat, region, migratory, and endemic breeding flags and merges them with the full bird dataset from birdlife.org
* bird_eda.ipynb: take final output from threats_habitats and combines with the diet data to form the final dataset. Prints out .info() and explores distribution of the target variable (threatened status)
* birds_simple_model.ipynb: very first logistic regression to make sure this problem is potentially interesting


## "Final" dataset description
* bird_dataset.csv
* Final records of 9,597. Datasets were merged on Scientific or English name (i.e., if one failed, try the other)
* Of the 9,597, there are 1,239 species that are considered Globally Threatened (Vulnerable, Endangered, or Critically Endangered)
* PassNonPass: Flag for whether or not the bird is passerine (perching) or not
* IOCOrder through Taxo: Various levels of Animal Kingdom clasification
* Diet-Inv through Diet-Plant0: Percent of overall diet that bird eats in each of these categories (should sum up to 1 for each species)
* Diet-5Cat: "general" classification of diet, i.e., omnivore, plantseed, etc
* ForStrat-watbelowsurf through ForStrat-aerial: Foraging (feeding) strategy. Should sum up to 1 for each species.
* Nocturnal: flag for whether the bird feeds at night or not
* BodyMass-Value: weight of the bird
* Global IUCN Red List Category: bird status per IUCN. 7 categories ranging from Extinct to Least Concern. They consider Vulnerable, Endangered, and Criticially Endangered as "Globally Threatened". This will form the bin that's our target outcome variable.
* Endemic_breeding: Is the bird endemic to a single country when breeding?
* Migratory: Is the bird migratory or not? If not, generally lives in the same location(s) throughout the year.
* Africa through South_amer: region flags for where these birds are generally seen. A species could have multiple region tags (e.g., many bird species breed in North America and winter in South America. Those would show up in both).
* agriculture_threat through transportation_threat: Flag from BirdLife international characterizing the nature of threats to a bird's habitat.
* artificial_terrestrial through wetlands_inland: habitat flags


## Other data

* There is additional region data found here (https://www.worldbirdnames.org/new/ioc-lists/master-list-2/)
* It is more useful for our model because it identifies primary "breeding" region, but the data is very messy.
* This is not included in the dataset, but we hope to have it incorporated by next week (if our dataset is approved :) )

## First simple model

In birds_simple_model.ipynb, we ran a logistic regression using most of the numerical columns. The model failed to converge and predicted a ton of false negatives. Seems like we have some work to do!
