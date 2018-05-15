## Cross Validation
- 머신러닝 알고리즘 수행시 데이터수가 작거나 모델의 견고함을 높이기 위해 Cross Validation 수행

### R
    library(cvTools)
    library ( foreach )

    R = 3
    K = 10
    cv <- cvFolds ( NROW ( iris ) , K = K , R = R )

    foreach ( r =1: R ) %do% {
      foreach ( k =1: K , .combine = c ) %do% {
      validation_idx <- cv $ subsets [ which ( cv $ which == k ) , r ]
        train <- iris [ - validation_idx , ]
        validation <- iris [ validation_idx , ]

        # preprocessing

        # training

        # prediction

        # estimating performance        

      }
    }

### Python
    Ready

### SparkML
    Ready
