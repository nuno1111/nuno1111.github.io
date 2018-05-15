## 결측치/이상치 처리
- 결측치 /이상치 탐색 및 처리

### R
    data(iris)
    head(iris)
    str(iris) # 데이터 구조
    summary(iris) # 데이터 기초 통계량

    #### 결측치 확인 ####
    anyNA(iris) # 결측치 존재여부 확인
    is.na(iris) # 전체 데이터 결측치 확인

    #### 이상치 확인 ####
    outlier_values <- boxplot(iris[,1:4]) # BOXPLOT에서 1.5 IQR 벗어난값 이상치로 판단
    outlier_values$out # 이상치 값 출력

### Python
    Ready

### SparkML
    Ready
