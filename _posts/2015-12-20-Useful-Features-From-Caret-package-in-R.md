---
layout: post
title: Useful features from CARET package in R
image: "/images/posts/feature_images/useful.jpg"
---


There are a lot of benefit using Caret package. These are my favorite things from this package.




## Parallel Processing

```R
library(doMC)
registerDoMC(cores = 5)

model <- train(y ~ ., data = training, method = "gbm")
```




## Spliting Data based on outcome.

```R
library(caret)
set.seed(3456)
trainIndex <- createDataPartition(iris$Species, p = .8,
                                  list = FALSE,
                                  times = 1)

irisTrain <- iris[ trainIndex,]
irisTest  <- iris[-trainIndex,]
```




## Model Training and Parameter Tuning

```R
fitControl <- trainControl(## 10-fold CV
                           method = "repeatedcv",
                           number = 10,
                           ## repeated ten times
                           repeats = 10)

gbm.model <- train(y ~ ., data = training, method = "gbm", trControl = fitControl)
rf.model <- train(y ~ ., data = training, method = "rf", trControl = fitControl)
svm.model <- train(y ~ ., data = training, method = "svmRadial", trControl = fitControl)
```



There are many benefits of using caret package. Check this link:[http://topepo.github.io/caret/index.html](http://topepo.github.io/caret/index.html)