## 앙상블 모형
- 안정적인 모델을 만들기 위해 여러 모델 조합
- Bagging
- Boosting
- RandomForest

### R
    idx <- sample(1:nrow(iris), nrow(iris) * 0.8)  # train set index 설정
    x.train <- iris[idx, -5]  # x data training set 분할
    y.train <- iris[idx, 5] # y data train set 분할
    x.test <- iris[-idx, -5] # x data test set 분할
    y.test <- iris[-idx, 5]# y data test set 분할  

    #Bagging
    library(ipred)
    fit.bagg <- ipredbagg(as.factor(y.train), x.train, data=train, nbagg=1000) #bootstrap의 개수 = 1000
    fit.bagg

    #예측
    pred<-predict(fit.bagg,x.test)
    table(pred,y.test)

    #오분류율
    mean(pred!=y.test)

    #확률예측
    pred2<-predict(fit.bagg,x.test,type="prob")
    head(pred2)

    # Boosting
    # install.packages("gbm")
    library(gbm)
    fit.boost <- gbm(as.factor(y.train)~.,data=x.train,distribution="multinomial",n.trees=1000)
    fit.boost

    #예측
    pred.prob<-predict(fit.boost,x.test,type="response",n.trees=1000)  #확률로 나옴
    pred.prob=matrix(pred.prob,ncol=3)                                 #각 범주의 확률

    #확률예측
    colnames(pred.prob) <- levels(y.train)
    head(pred.prob)

    # 가장 높은 확률을 가진 범주로 분류
    pred<-apply(pred.prob,1,which.max)
    pred<-ifelse(pred==1,"High",ifelse(pred==2,"Low",ifelse(pred==3,"Middle","very_low")))
    table(pred,y.test)

    #오분류율
    mean(pred!=y.test)

    ##### Random Forest
    library(randomForest)
    fit.rf <- randomForest(as.factor(y.train)~.,data=x.train, ntree=1000, mtry=3)   #변수선택 k를 3로 설정

    #예측
    pred<-predict(fit.rf,x.test)
    table(pred,y.test)

    #오분류율
    mean(pred!=y.test)

### Python
    Ready

### SparkML
    Ready
