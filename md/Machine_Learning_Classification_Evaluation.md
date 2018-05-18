## 분류모델평가
- 분석목적에 따라 분류모델의 다양한 평가방법존재

### R
    data <- iris[iris$Species != 'setosa',] # 3종에서 1종제거
    data$Species <- as.factor(as.character(data$Species)) # factor값 재지정

    logistic.fit <- glm( Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = data, family = binomial)


    pred_species <- predict(logistic.fit, newdata = data, type = "response")

    cut <- ifelse(pred_species >= 0.5, "virginica", "versicolor") ## 절단값 0.5로 설정

    predicted <- cut
    actual <- data$Species

    # confusionMatrix()
    table(predicted, actual)

    # Accuracy 계산
    sum ( predicted == actual ) / NROW ( actual )

    # caret의 confusionMatrix()
    library(caret)
    (cm <- confusionMatrix ( predicted , actual ))
    cm$overall[ "Accuracy" ]

    # ROC
    library(ROCR)
    # pr <- prediction(pre, test$LABEL)
    pr <- prediction(pred_species, actual)
    prf <- performance(pr, measure = "tpr", x.measure = "fpr")
    plot(prf)

    auc <- performance(pr, measure = "auc")
    auc <- auc@y.values[[1]]
    auc
### Python
    Ready

### SparkML
    Ready
