## 로지스틱 회귀
- 이진분류모델의 가장 대표적인 알고리즘

### R
    data <- iris[iris$Species != 'setosa',] # 3종에서 1종제거
    data$Species <- as.factor(as.character(data$Species)) # factor값 재지정

    # 로지스틱 회귀모형식
    logistic.fit <- glm( Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = data, family = binomial)

    # 분류표
    pred_species <- predict(logistic.fit, newdata = data, type = "response")

    cut <- ifelse(pred_species >= 0.5, "virginica", "versicolor") ## 절단값 0.5로 설정
    (result <- table(data$Species, cut))

    # 정분류율
    (accuracy <- (result[1, 1] + result[2, 2]) / sum(result) * 100)
    
### Python
    Ready

### SparkML
    Ready
