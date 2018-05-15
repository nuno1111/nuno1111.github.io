## Data Scaling
- 거리계산 필요한 알고리즘에는 사전 스케일링 필요
- K-Means 포함 다수 Clustering 포함 주성분 분석 및 DeepLearing 등에도 필요

### R
    # 0 ~ 1 사이
    library(scales)
    rescale(iris[,1])

    # 표준정규화
    scale(iris[1:4])

### Python
    Ready

### SparkML
    Ready
