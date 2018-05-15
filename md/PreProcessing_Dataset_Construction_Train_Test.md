## Train Test DataSet 생성
- 머신러닝 알고리즘 수행전에 Train Set과 Test Set을 일정 비율로 나누는 작업

### R
    idx <- sample(1:nrow(iris), nrow(iris) * 0.7)  # train set index 설정
    train_df <- iris[idx, ]  # train set 분할
    test_df <- iris[-idx, ]  # test set 분할

### Python
    Ready

### SparkML
    Ready
