# forensicRadiomics-liver
Scripts, tools and methods for Radiomics in Forensic liver-examination.

In the *models* folder you can find the three dicotomic-randomForest-classifiers aimed at estimating if

* the patients died before/after 12h
* the patients died before/after 24h
* the patients died before/after 36h

The models are trainded with the randomforest package: you can find further information about how to use that object at: https://cran.r-project.org/web/packages/randomForest/index.html

An example of input file, can be found in the *./models/example.input.dataset.RData*

## fast testing

To easily test the model, let's assume you want to test the second patient in the *example.input.dataset.RData* dataset.

you can easily test it with:


```
library(randomForest)
load(file = "./models/RandomForest.out_24.RData")
load(file = "./models/example.input.dataset.RData")

predict( RF, newdata = example.input.dataset)
```

