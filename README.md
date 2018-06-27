# BarleyMarkerValidation
MSDS 692 Barley Marker Validation Project

# Project Overview
Barley is a key ingredient in brewing beer. It is also an important cereal grain that provides some food to humans, but mostly to livestock. I work for a large beer company breeding barley. Our goal is to improve the barley varieties available  to brewers and farmers. The barley needs to produce good beer, but it also needs to be profitable for the farmer. New varieties are slow to produce with a new line taking about 14 years to be commercially grown after first being made. It then takes another one to two years to make it into large scale beer production. With a global environment that is changing, 15 years is a long time and many varieties are abandoned long before making it to market.

In order to help speed up the process, and make it more accurate, genetic assisted selection is starting to be used. This is different from genetically modifying in that the genes are not physically altered by man made processes, instead plants are screened to identify the genes they contain. Only the plants with desirable genes continue through the pipeline. The biggest problem currently is we do not know what genes are associated with what traits. It is quickly being mapped by academics, but they are generally looking at barley that is different from what we have. Academics use many types of barley in their research, like feed barley. From papers and research institutions there are approximately 200 genes associated with traits.

The goal of this project is to validate DNA markers used in barley breeding at my company. The genes are commonly referred to as markers. The markers currently used were determined from looking at barley varieties used by academia. To be useful to the company where I work, the markers need to be correlated to physical traits with our varieties. Basically, we need to see if the markers identified by academia to be associated to certain traits are also associated with those traits in our 'in house' varieties.

Select varieties were screened in 2015. As the breeding process progresses, varieties determined to be less desirable are dropped.  The data set has physical observations from 2015, 2016, and 2017, however, 2016 and 2017 do not contain all the varieties that were in 2015. More over, the malt analysis lab did not run tests on varieties. The varieties, for the most part, should be genetically fixed for every trait. This means that every variety should be homozygous for every marker and we will make the assumption that there are only two alleles (choices) for each gene. Barley is diploid, like humans, meaning that there are two of every chromosome which make the genetics much easier because there are less dominance issues. Being homozygous at every marker means that each marker within a given line should have two copies of the same allele. For each marker there should be two populations of varieties, one with one homozygous set of alleles and one with the other homozygous set of alleles.

In addition to the genetic make up of the variety, the environment where it is grown can have a huge impact on the physical characteristics. Years to year, the same field can produce very different barley from the same variety. For this study, each growing location and crop year made up one trial.

The bulk of the analysis to determine if a physical trait was associated with a marker, t-tests were used. For each marker there were two populations, one with alleles "AA" and the other with alleles "BB" for that marker. Genetic testing is extremely accurate, but sometimes errors do occur where the sample cannot be determined. For those instances I used K-nearest neighbor, using physical traits to classify the missing genetic information. Similarly, with lab test sometimes errors occur resulting in "NA" values. For these, I used K-nearest neighbor to imputate the data.

# EDA
Once I started looking at the data it was apparent that the different trials would need to be comparable. To do this I normalized the data within each trial, for each trait. From the database, there was one file for physical traits measured by the lab, and another file for physical traits measured in the field.
![Beta Glucan EDA] 


# Analysis
First, I ran t-tests where I compiled the normalized values from every trial for each marker and trait. I then divided them into two groups based on marker allele (HAP_CALL). For each marker and trait I then ran a t-test. This resulted in way too much being significant.

I determined that the reason for so much appearing significant was the degrees of freedom for each t-test was very high. To reduce the degrees of freedom I determined the sub-set of normalized values for each marker and trial for each trait and then averaged them to create a smaller sample, with the same characteristics as the previous population.

To run the k-nearest neighbor machine learning I transformed the data. This is where the lab not having results for every trial became a problem. The table was sparsely populated enough that knn did not work. I filtered out all the trials that the lab did not run and I got a data frame that was compatible with knn. I first ran the knn imputations.

Then I ran the knn classification.
# Conclusions

# References
 link to video
