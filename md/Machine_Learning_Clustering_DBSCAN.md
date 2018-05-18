## DBSCAN 군집화
- 밀도기반 군집 알고리즘

### R
    data(iris)
    iris <- scale(as.matrix(iris[,1:4]))

    library(dbscan)

    kNNdist(iris, k=4, search="kd")
    kNNdistplot(iris, k=4) ## the knee is around a distance of .5

    cl <- dbscan(iris, eps = .5, minPts = 4)
    pairs(iris, col = cl$cluster+1L) ## Note: black are noise points

    newdata <- as.matrix(iris[110:120,])
    predict(res, newdata, iris)

### Python
    Ready

### SparkML
    Ready
