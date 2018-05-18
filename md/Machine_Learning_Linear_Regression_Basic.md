## Linear Regression
- 다중 선형회귀 분석을 위한 기본소스

### R
    # Sepal.Length 값을 예측하는 회귀분석 수행
    reg_model <- lm(Sepal.Length ~ ., data=iris)

    reg_model$coefficients # 계수
    reg_model$residuals    # 잔차

    summary(reg_model) # 회귀분석 결과 정보
    # p-value < 0.01이므로 유의미한 모델

    # 개발된 모델로 예측
    predict(reg_model)

### Python
    Ready

### SparkML
    Ready
