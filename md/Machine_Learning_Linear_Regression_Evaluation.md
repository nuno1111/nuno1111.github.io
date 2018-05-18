## 선형회귀 평가
- 다중 선형회귀 모델에 대한 평가방법
- R-squared : SSR / SST
- Adjusted R-squared : 모델복잡성(변수개수) 고려
- AIC
- BIC

### R
    reg_model <- lm(Sepal.Length ~ ., data=iris) # 모델생성

    # R2, Adjusted R2
    summary(reg_model) # summary 하단 R2, Adjusted R2 확인

    # AIC
    AIC(reg_model)

    # BIC
    BIC(reg_model)
### Python
    Ready

### SparkML
    Ready
