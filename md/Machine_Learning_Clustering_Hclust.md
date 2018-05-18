## Hclust
- 계층적 군집화
- 최단연결법
- 최장연결법

### R
    x <- scale(iris[1:4])
    label <- iris$Species

    hc1 <- hclust(dist(x)^2, method = "single")   #최단 연결법
    plot(hc1, labels = label, hang = 1, main = "dendrogram : 최단 연결법")

    hc2 <- hclust(dist(x)^2, method = "complete")   #최장 연결법
    plot(hc2, labels = label, hang=1, main = "dendrogram : 최장 연결법")

    c1.num <- 3  #군집 수 설정
    hc1.result <- cutree(hc1, k = c1.num) #최단 연결법 결과
    names(hc1.result) <- label
    hc1.result

    # 그룹 별 산점도로 결과 확인
    plot(x, pch = hc1.result, col = label, main = "single")
    text(x, labels = label, adj = -0.1, cex = 0.8)

    hc2.result <- cutree(hc2, k = c1.num) #최장 연결법 결과
    names(hc2.result) <- label
    hc2.result

    # 그룹 별 산점도로 결과 확인
    plot(x, pch =  hc2.result, col = label, main = "complete")
    text(x, labels = label, adj = -0.1, cex = 0.8)

### Python
    Ready

### SparkML
    Ready
