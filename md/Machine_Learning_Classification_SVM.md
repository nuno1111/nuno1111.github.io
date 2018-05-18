## SVM
- 주어진 data의 클래스를 고려할때, 각 클래스를 나눌 수 있는 초평면을 구하는 알고리즘
- 선형
  - Linear
- 비선형
  - Radial
  - Sigmoid
  - Polynomial

### R
    # install.packages("e1071")
    library(e1071)  

    fit.svm.linear <- svm(Species~., iris, kernel = "linear")  # kernel: linear,sigmoid,polynomial
    fit.svm.linear

    ##### Classification Plot
    plot(fit.svm.linear, iris, Petal.Width ~ Petal.Length)

    ### 모형 Tuning
    obj.linear <- tune.svm(Species~., data=iris, kernel="linear", gamma=2^(-7:7), cost=2^(-7:7))  # 선형 svm tuning
    obj.linear$best.model  # tuning 한 best model 출력

    ### 모형 Test
    pred.linear<-predict(obj.linear$best.model, iris)

    ### 모형 정확도 확인
    table(pred.linear, iris$Species)  # confusion matirx 출력
    acc <- sum(diag(table(pred.linear, iris$Species)))/ sum(table(pred.linear, iris$Species)) # 정확도 계산
    cat("모형 정확도 : ", round(acc*100, 2), "%", "\n")  # 정확도 출력
    # 선형 SVM을 통한 분류 정확도 91.03%로 나타남

    ### 선형 SVM Classfication Plot
    plot(obj.linear$best.model, iris, Petal.Width ~ Petal.Length)


### Python
    Ready

### SparkML
    Ready
