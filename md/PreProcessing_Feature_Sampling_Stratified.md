## Stratified Sampling
- 층화 추출 : 샘플링시 다수 그룹에
- 복원/비복원 추출
- 가중치 추출 등

### R
    # install.packages("sampling")
    library(sampling)

    x <- strata(iris, c("Species"), size=c(3,3,3), method="srswor") # 각 종류별 3개씩 추출
    x

    # method 종류
    # srswor : simple random sampling without replacement
    # srswr : simple random sampling with replacement
    # poisson : Poisson sampling
    # systematic : systematic sampling

### Python
    Ready

### SparkML
    Ready
