## Random Sampling
- 데이터가 많아서 성능 효율화가 필요한 경우 샘플링 수행
- 복원/비복원 추출
- 가중치 추출 등

### R
    sample(1:10,5)
    sample(1:10,5,replace = T) # 복원추출
    sample(1:10,5,replace = T,prob = 1:10) # 복원추출  + 가중치
    sample(1:10) # 데이터 셔플링 효과

### Python
    Ready

### SparkML
    Ready
