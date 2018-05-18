## 다중공선성
- 다중 선형회귀 모델에 다중공선성 검사
- VIF(Variance inflation factor)
- 상태지수(Condition Number)


### R
    reg_model <- lm(Sepal.Length ~ ., data=iris[1:4]) # 모델생성, vif는 feature가 연속형 변수로만 구성

    # vif
    library(car)
    vif(reg_model)
    # vif 값이 10 이상일 겨우  다중공선성 있다고 판단 (5이상을 보는 경우도 있음)

    # condition number
    X=model.matrix(reg_model)[,-1] # Intercept 제거
    sqrt(eigen(cor(X))$values[1]/eigen(cor(X))$values)
    # condition number 값이 10 이상일 겨우 다중공선성 경계필요
    # condition number 값이 100 이상일 겨우 다중공선성 문제심각

### Python
    Ready

### SparkML
    Ready
