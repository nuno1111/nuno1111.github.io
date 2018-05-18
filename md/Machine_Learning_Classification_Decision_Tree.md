## 의사결정트리
- 다중분류모델중 모델이 단순하여 예측력은 떨어지지만 설명력이 분류알고리즘

### R
    #tree
    library(tree)
    tree_ml<-tree(Species~., data=iris, split="deviance")
    # tree_ml<-tree(Species~., data=iris, split="gini")
    tree_ml
    plot(tree_ml)
    text(tree_ml)
    summary(tree_ml)

    #tree 가지치기
    cv.trees<-cv.tree(tree_ml, FUN=prune.misclass )
    plot(cv.trees) # 오분류 가장 적은 노드수 확인

    prune.trees <- prune.misclass(tree_ml, best=4)
    plot(prune.trees)
    text(prune.trees, pretty=0)

    #tree 예측
    yhat  <- predict(prune.trees, newdata=iris, type="class")
    table(yhat,iris$Species) # confusion matrix
    cat("정분류율 = ",sum(yhat==iris$Species)/length(yhat),"%")

    #CART
    library(rpart)
    library(rpart.plot)

    cart_ml <- rpart(Species~., data=iris)
    cart_ml
    plot(cart_ml)
    text(cart_ml, all=T)

    #CART - 시각적인 그래프
    prp(cart_ml, type=4, extra=1, digits=3)

    #CART - 예측
    yhat  <- predict(cart_ml, newdata=iris, type="class")
    ytest <- iris$Species
    table(yhat,ytest)
    cat("오분류율 = ",sum(yhat!=ytest)/length(yhat),"%")

    #C5.0
    library(C50)
    c5_ml  <- C5.0(Species~., data=iris)
    summary(c5_ml)
    plot(c5_ml)

    #C5.0 - 예측
    yhat  <- predict(c5_ml, newdata=iris, type="class")
    ytest <- iris$Species
    table(yhat,ytest)
    cat("오분류율 = ",sum(yhat!=ytest)/length(yhat),"%")

    #QUESET
    library(party)

    queset_ml <- ctree(Species~., data=iris, controls = ctree_control(testtype=c("Bonferroni")))
    summary(queset_ml)
    plot(queset_ml)

    #QUESET - 예측
    yhat  <- predict(queset_ml, newdata=iris, type="response")
    ytest <- iris$Species
    table(yhat,ytest)
    cat("오분류율 = ",sum(yhat!=ytest) / length(yhat), "%")

### Python
    Ready

### SparkML
    Ready
