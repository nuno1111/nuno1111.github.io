## 선형회귀분석 정규화
- 안정적인 선형회귀모델을 만들기 위한 정규화 방법
- Ridge
- LASSO
- ElasticNet

### R
    # install.packages("glmnet")
    library(glmnet)

    x <- model.matrix(Sepal.Length~., iris)[,-1]
    y <- iris$Sepal.Length

    lm_mod <- lm(Sepal.Length~.,iris)
    coef(lm_mod)
    predict(lm_mod)

    # Ridge
    cv.ridge <- cv.glmnet(x, y, alpha = 0)
    plot(cv.ridge)
    coef(cv.ridge, s=cv.ridge$lambda.min)
    predict(cv.ridge,newx = x)

    # Lasso
    cv.lasso <- cv.glmnet(x, y, alpha = 1)
    plot(cv.lasso)
    coef(cv.lasso, s=cv.lasso$lambda.min)
    predict(cv.lasso, newx = x)

    # ElasticNet
    cv.elanet <- cv.glmnet(x, y, alpha = 0.5) # 0 ~ 1 사이값
    plot(cv.elanet)
    coef(cv.elanet, s=cv.elanet$lambda.min)
    predict(cv.elanet, newx = x)

### Python
    Ready

### SparkML
    Ready
