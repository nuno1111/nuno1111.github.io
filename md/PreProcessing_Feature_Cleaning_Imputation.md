## 결측치/이상치 처리
- 결측치/이상치 제거
- 결측치/이상치 보정
- 중앙값 보정
- KNN 보정

### R
    #### 이상치 확인 ####
    outlier_values <- boxplot(iris[,1:4]) # BOXPLOT에서 1.5 IQR 벗어난값 이상치로 판단
    outlier_values$out # 이상치 값 출력

    #### 이상치를 결측치로 변경 ####
    iris[iris$Sepal.Width %in% outlier_values$out,]$Sepal.Width <- NA

    anyNA(iris) # 결측치 존재여부 확인
    is.na(iris) # 전체 데이터 결측치 확인

    #### 결측치 제거 ####
    iris_NA_remove <- iris[complete.cases(iris),]

    #### 중앙값 보정 ####
    iris_NA_mean <- iris
    iris_NA_mean[is.na(iris_NA_mean$Sepal.Width),]$Sepal.Width <- median(iris_na$Sepal.Width , na.rm = TRUE ) # 중앙값 구해서 보정

    # install.packages("DMwR")
    library(DMwR)
    iris_centralImputation <- centralImputation ( iris [1:4]) # 중앙값 대치 패키지 이용
    iris_centralImputation[is.na(iris$Sepal.Width),] # 보정값 확인

    #### KNN 보정 ####
    iris_KNNImputation <- knnImputation( iris[1:4])
    iris_KNNImputation[is.na(iris$Sepal.Width),] # 보정값 확인

    boxplot(iris_KNNImputation[1:4]) # 보정결과 확인

### Python
    Ready

### SparkML
    Ready
