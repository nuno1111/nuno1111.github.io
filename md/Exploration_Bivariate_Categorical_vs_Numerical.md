## 범주형-이산형 변수간 관계 탐색
- 범주형 변수와 이산형 변수간 관계 탐색 방법
- T-검정
- ANOVA

### R
    head(iris)
    summary(iris)

    # 단일 표본 T-검정 수행
    t.test(iris$Sepal.Length , alternative = "two.sided", mu = 5.8)
    # p-value > 0.05 이므로 유의수준 0.05 하에 귀무가설 기각하지 못함
    # 평균은 5.8 이라고 할 수 있음

    iris_temp = iris[iris$Species != 'virginica',] # 3종에서 1종제거
    iris_temp$Species <- as.factor(as.character(iris_temp$Species)) # factor값 재지정

    # 이표본 T-검정 수행
    t.test(Sepal.Length ~ Species, alternative = "two.sided", data = iris_temp)
    # p-value < 0.005 이므로 유의수준 0.01 하에 귀무가설 기각
    # 두 표본 평균은 다르다고 할 수 있음

    # Anova (3표본 이상인 경우)
    aov_m <- aov(Sepal.Width~Species, data=iris)
    summary(aov_m)
    # p-value < 0.005 이므로 유의수준 0.01 하에 귀무가설 기각
    # "iris의 품종(Species) 별로 Sepal.Width 평균은 다르다”라고 판단

    # Chart
    boxplot(Sepal.Width~Species, data = iris)

### Python
    Ready

### SparkML
    Ready
