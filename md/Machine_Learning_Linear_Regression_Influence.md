## 영향점 확인
- 선형회귀모델 생성 후 영향점 파악
- 이상점
  - 산점도 확인
  - 표준화된 잔차의 절대값이 3이상
- 영향점
  - Cook's Distance

### R
    reg_model <- lm(Sepal.Length ~ ., data=iris) # 모델생성

    #influence measure
    influence.measures(reg_model)
    influencePlot(reg_model
        ,id.method='identify'
        ,main='influence plot'
        ,sub='circle size is proportional to Cooks distance')

    par(mfrow=c(2,2));plot(reg_model) # plot을 통해 이상점 확인가능


### Python
    Ready

### SparkML
    Ready
