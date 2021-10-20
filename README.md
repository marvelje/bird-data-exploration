## Bird Data Summary

This readme summarizes a consolidated dataset of ~10K bird species that includes diet information, size, habitat, threatened status, nature of threat, and other bird characteristics.
<br />
## Business Problem



## Sources

Diet:
* Paper: https://figshare.com/collections/EltonTraits_1_0_Species-level_foraging_attributes_of_the_world_s_birds_and_mammals/3306933
* Github: https://github.com/hurlbertlab/dietdatabase
<br />
Other bird features:
* Data Dictionary: http://datazone.birdlife.org/species/spcrange
* Data Query Portal: http://datazone.birdlife.org/species/search
* Main Website: https://www.birdlife.org
<br />
Red List:
* https://www.iucnredlist.org



## "Final" dataset description
* bird_dataset.csv
* PassNonPass: Flag for whether or not the bird is passerine (perching) or not
* IOCOrder through Taxo: Various levels of Animal Kingdom clasification
* Diet-Inv through Diet-Plant0: Percent of overall diet that bird eats in each of these categories (should sum up to 1 for each species)
* Diet-5Cat: "general" classification of diet, i.e., omnivore, plantseed, etc
* ForStrat-watbelowsurf through ForStrat-aerial: Foraging (feeding) strategy. Should sum up to 1 for each species.
* Nocturnal: flag for whether the bird feed at night or not
* BodyMass-Value: weight of the bird
* Global IUCN Red List Category: bird status per IUCN. 7 categories ranging from Extinct to Least Concern. They consider Vulnerable, Endangered, and Criticially Endangered as "Globally Threatened". This will form the bin that's our target outcome variable.
* Endemic_breeding: Is the bird endemic to a single country when breeding?
* Migratory: Is the bird migratory or not? If not, generally lives in the same location(s) throughout the year.
* Africa through South_amer: region flags for where these birds are generally seem. A species could have multiple region tags (e.g., many bird species breed in North America and winter in South America. It would show up in both).
* agriculture_threat through transportation_threat: Flag from BirdLife international characterizing the nature of threats to a birds habitat.
* artificial_terrestrial through wetlands_inland: habitat flags


## Other data

* There is additional region data found here (https://www.worldbirdnames.org/new/ioc-lists/master-list-2/)
* It is more useful for our model because it identifies primary "breeding" region, but the data is very messy.
* This is not included in the dataset, but we hope to have it incorporated by next week (if our dataset is approved :) )
