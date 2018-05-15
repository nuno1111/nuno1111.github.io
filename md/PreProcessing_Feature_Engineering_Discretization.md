## 연속형 데이터 범주화
- 연속형 데이터의 간격 혹은 빈도 기준으로 범주화 하는 방법

### R
    x <- iris[,1]
    library(arules)

    #### 동일빈도 ####
    disc <- discretize(x, breaks = 3, labels = c('A','B','C'))

    #### 동일간격 ####
    disc <- discretize(x, method = "interval", breaks = 3, labels = c('A','B','C'))

    #### k-means clustering ####
    disc <- discretize(x, method = "cluster", breaks = 3, labels = c('A','B','C'))

    #### 사용자지정 ####
    disc <- discretize(x, method = "fixed", breaks = c(4.3, 5.5, 6.5, 7.9), labels = c('A','B','C'))

### Python
    Ready

### SparkML
    Ready
