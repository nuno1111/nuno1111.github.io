## 잔차분석
- 선형회귀모델 생성 후 모델 적합성 검사를 위해 잔차분석 수행
- 독립성검정
  - Durbin-Watson
- 정규성검정
  - Q-Q Plot
  - Shapiro-Wilk Test
  - Anderson-darling test
  - Kolmogorov-Smirnov Test
  - Jarque-Bera 검정
- 등분산성
  - Breusch-Pagan

### R
    reg_model <- lm(Sepal.Length ~ ., data=iris) # 모델생성

    # install.packages("car")
    library(car)

    # 1. 독립성 (Durbin-Watson 통계량)
    durbinWatsonTest(reg_model)
    #- D-W 통계량 = 2에 가까울수록 오차항 독립
    #- 귀무가설 : 독립이다.

    # 2-1. 정규성 (Q-Q Plot)
    e <- iris$Sepal.Length - predict(reg_model)
    qqnorm(e); qqline(e, col="red")

    # 2-2. 정규성 (jarque bera)
    # install.packages("tseries")
    library(tseries)
    jarque.bera.test(resid(reg_model)) # 모델에서 잔차 뽑아내기 : resid(reg_model)
    qchisq(0.05,df=2,lower.tail=F) # 5% 유의수준의 임계값
    # X-squared < 5.991465 이기 때문에 정규분포를 따른다.

    # 2-3. 정규성 (Shapiro-Wilk Test)
    shapiro.test(resid(reg_model))
    # H0=정규분포를 따른다.

    # 2-4. 정규성 (Anderson-darling test)
    # install.packages("nortest")
    library(nortest)
    ad.test(resid(reg_model))
    # H0=정규분포를 따른다.

    # 3. 등분산성 (Breusch-Pagan Test)
    # install.packages("lmtest")
    library("lmtest")
    bptest(reg_model)
    # H0 = 등분산성이 있다.
    # p-value > 0.05 : 귀무가설을 기각하지 못하므로 등분산성 존재

    par(mfrow=c(2,2));plot(reg_model) # plot을 통해 잔차 및 정규성 확인가능

### Python
    Ready

### SparkML
    Ready
