## K-means 군집화
- 사전에 군집수(k)를 정하고 각 개체는 가장 가까운 군집중심에 할당
- 군집중심을 이동하여 새로운 군집을 구성하고 각 개체별 거리가 최소가 되도록 이동

### R
    x <- scale(iris[1:2])
    label <- iris$Species

    k_mod <- kmeans(x ,centers = 3) # 3개 군집

    table(label,k_mod$cluster)

    (kc <- table(k_mod$cluster))
    plot(x, pch = k_mod$cluster, col = k_mod$cluster, main = "K-means clustering")
    plot(x, pch = k_mod$cluster, col = label, main = "K-means clustering")

### Python
    Ready

### SparkML
    Ready
