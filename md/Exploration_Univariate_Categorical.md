## 범주(이산)형 단일 변수 탐색
- 하나의 범주(이산)형 변수에 대한 여러 탐색방법

### R
    data(iris)
    head(iris)
    summary(iris) # 전반적 기초 통계량

    table(iris$Species) # 범주형 변수 Count

    # Chart
    barplot(table(iris$Species))
    pie(table(iris$Species))

### Python
    Ready

### SparkML
    Ready
