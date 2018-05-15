## 연속형 변수간 관계 탐색
- 두 연속형 변수간에 관계 탐색 방법
- 상관계수(Correlation)

### R
    ### 상관계수
    # 두 확률 변수 사이의 관계를 파악

    # 피어슨 상관계수(Pearson Correlation Coefficient)
    # 피어슨 상관계수는 [-1, 1] 사이의 값
    # 1차 선형관계 판별

    cor(iris$Sepal.Width, iris$Sepal.Length)
    cor(iris[ ,1:4])

    # 스피어만 상관계수(Spearman’s Rank Correlation Coefficient)
    # 상관계수를 계산할 두 데이터의 실제값 대신 두 값의 순위를 사용

    # Hmisc::rcorr() : 피어슨 / 스피어만 상관계수 모두 가능한 패키지
    library(Hmisc)

    m <- as.matrix(iris[ ,1:4])
    rcorr(m , type="pearson")$r
    rcorr(m , type="spearman")$r

    # Chart
    plot(iris$Sepal.Width, iris$Sepal.Length)

### Python
    Ready

### SparkML
    Ready
