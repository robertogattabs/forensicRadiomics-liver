# forensicRadiomics-liver
Scripts, tools and methods for post-PMCT radiomic analysis of the liver.


## Content

In the *./models* folder you can find the three dicotomic randomForest classifiers aimed at estimating if:


* the patients died before/after 12h ( *./models/RandomForest.out_12.RData* )
* the patients died before/after 24h ( *./models/RandomForest.out_24.RData* )
* the patients died before/after 36h ( *./models/RandomForest.out_36.RData* )

The models are trained with the R randomforest package; you can find further information on how to use such package at the link: https://cran.r-project.org/web/packages/randomForest/index.html

An example of input file can be found in the  *./models/example.input.dataset.RData*.  If you wish to use the models on your dataset, you **must structure it exactly like the sample input file**.

## Fast testing

Assume you want to test the second subject in the *./models/example.input.dataset.RData* dataset to know if he/she died before/after 24h.

This task can easily be achieved with the following script:



```
library(randomForest)
load(file = "./models/RandomForest.out_24.RData")
load(file = "./models/example.input.dataset.RData")

testingPatient <- 2

a <- predict( RF, newdata = example.input.dataset[testingPatient,])
result <- levels(a)[a]
```

The variable *result* will be set to *0* if the subject is estimated to have died before the 24h or, on the contrary, it will be set to *1*.



## Important note

The features should be extracted with a radiomics software IBSI compliant ( see: https://theibsi.github.io/ ). In our specific case, we used moddicom[1] ( https://github.com/kbolab/moddicom )

## Contacts

For any questions, issues or further information about this project: *fabio.degiorgio@unicatt.it*

## References

```
[1] Zwanenburg A, Vallières M, Abdalah MA, Aerts HJWL, Andrearczyk V, Apte A, Ashrafinia S, Bakas S, Beukinga RJ,
Boellaard R, Bogowicz M, Boldrini L, Buvat I, Cook GJR, Davatzikos C, Depeursinge A, Desseroit MC, Dinapoli N, Dinh CV,
Echegaray S, El Naqa I, Fedorov AY, Gatta R, Gillies RJ, Goh V, Götz M, Guckenberger M, Ha SM, Hatt M, Isensee F,
Lambin P, Leger S, Leijenaar RTH, Lenkowicz J, Lippert F, Losnegård A, Maier-Hein KH, Morin O, Müller H, Napel S,
Nioche C, Orlhac F, Pati S, Pfaehler EAG, Rahmim A, Rao AUK, Scherer J, Siddique MM, Sijtsema NM, Socarras Fernandez J,
Spezi E, Steenbakkers RJHM, Tanadini-Lang S, Thorwarth D, Troost EGC, Upadhaya T, Valentini V, van Dijk LV, van
Griethuysen J, van Velden FHP, Whybra P, Richter C, Löck S. The Image Biomarker Standardization Initiative:
Standardized Quantitative Radiomics for High-Throughput Image-based Phenotyping. Radiology. 2020 May;295(2):328-338.
doi: 10.1148/radiol.2020191145. Epub 2020 Mar 10. PMID: 32154773; PMCID: PMC7193906.

[2] Dinapoli N, Alitto AR, Vallati M, Gatta R, Autorino R, Boldrini L, Damiani A, Valentini V. Moddicom: a complete and
easily accessible library for prognostic evaluations relying on image features. Annu Int Conf IEEE Eng Med Biol Soc.
2015 Aug;2015:771-4. doi: 10.1109/EMBC.2015.7318476. PMID: 26736376.
```
