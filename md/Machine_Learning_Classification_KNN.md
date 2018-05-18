## KNN
 - 가장 가까운 K개의 집단중에서 최대개수의 집단으로 분류

### R
    idx <- sample(1:nrow(iris), nrow(iris) * 0.8)  # train set index 설정
    tr_x_df <- iris[idx, -5]  # x data training set 분할
    tr_y_df <- iris[idx, 5] # y data train set 분할
    ts_x_df <- iris[-idx, -5] # x data test set 분할
    ts_y_df <- iris[-idx, 5]# y data test set 분할  

    # library 불러오기
    library(class)

    k.grid <- seq(1 ,21, 2) # k에 대한 1 부터 21까지 홀수 grid 생성

    acc <- c() # 모형 정확도 저장 공간 생성

    # k에 따른 모형 정확도 계산 loop
    for(i in k.grid){
      knn_model <- knn.cv(tr_x_df, k = i, cl = tr_y_df) # k에 따른 모형 적합
      error <- sum(knn_model == tr_y_df) / nrow(tr_x_df) # 각 k에 대한 정확도 계산
      acc <- c(acc, error) # 전체 k에 대한정확도 저장
    }

    plot(k.grid, acc, type = "b") # k에 대한 모형 정확도 plot
    (optimal.k <- k.grid[which.max(acc)]) # 가장 높은 모형 정확도를 가진 k 확인

    knn_model <- knn(train = tr_x_df, test = ts_x_df, cl = tr_y_df, k = optimal.k) # optimal k를 통한 모형 Test
    table(knn_model, ts_y_df) # Test Confusion Matrix
    sum(diag(table(knn_model, ts_y_df))) / length(ts_y_df) # Test 정확도 계산

### Python
    Ready

### SparkML
    Ready
