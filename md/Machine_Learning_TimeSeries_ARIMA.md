## 시계열분석
- 시간의 흐름에 따라 기록된 데이터를 분석
- STL(Seasonal Trend Decomposition Using Loess)
- ARIMA

### R
    library(forecast)

    origin <- AirPassengers

    plot(origin)
    # 데이터의 이분산과 1차 추세가 존재함
    # 분산 안정화를 위한 Box Cox 변환과 1차 차분 필요

    plot(decompose(origin)) # Decomposition

    # 분산 안정화 및 차분
    tran_org <- BoxCox(origin, BoxCox.lambda(origin)) # 분산안정화
    plot(tran_org)
    tran_diff_org <- diff(tran_org) # 차분
    plot(tran_diff_org)

    # ACF, PACF를 통한 탐색
    acf(tran_diff_org, lag.max=24)
    pacf(tran_diff_org, lag.max=24)

    # 계절 차분 및 ACF, PACF를 통한 탐색
    tran_sdiff_org <- diff(tran_diff_org, lag = 12) # 계절차분
    plot(tran_sdiff_org)

    acf(tran_sdiff_org, lag.max = 24)
    # acf는 lag=1,3,12에서 0이 아닌값 가짐  비계절 시차 4부터 절단 -> MA(3), 계절 -> 시차 2부터 절단 SMA(1)

    pacf(tran_sdiff_org, lag.max = 24)
    # 시차 2와 8에서 0보다 큰 값을 가지지만 정확한 모형을 찾기 위해 auto.arima를 통해 aic가 최소가 되는 order 값 구함

    auto.arima(tran_sdiff_org, max.p = 3, max.q=3, max.Q=1)

    # 모형 구축
    model_arima <- arima(tran_org, order=c(0,1,1), seasonal = list(order = c(0,1,1), period = 12))

    # 잔차 검정
    tsdiag(model_arima)

    # 독립성 검정
    Box.test(model_arima$residuals, type="Ljung-Box")
    # 잔차의 독립성, 등분산성, 정규성 만족

    # 원 데이터 및 fitted 데이터의 비교
    plot(spline(time(origin), origin),type='l',xlab='Time',ylab='Pop')
    lines(InvBoxCox(fitted(model_arima), BoxCox.lambda(origin)), col='red')
    mean((origin - InvBoxCox(fitted(model_arima), BoxCox.lambda(origin)))^2)

    # 12개월 예측
    arima_fit <- predict(model_arima, n.ahead=12) #BoxCox 변환 데이터 사용
    lambda <- BoxCox.lambda(origin)
    ts.plot(origin, xlim=c(1950,1965), ylim = c(0, 1000))
    lines(InvBoxCox(arima_fit$pred, lambda),col="red")
    lines(InvBoxCox(arima_fit$pred+1.96*arima_fit$se, lambda),col="blue",lty=1)
    lines(InvBoxCox(arima_fit$pred-1.96*arima_fit$se, lambda),col="blue",lty=1)

    # test
    auto.arima(origin)
    model_arima <- arima(tran_org, order=c(2,1,1), seasonal = list(order = c(0,1,0), period = 12))
    plot(forecast(model_arima,h=120))


### Python
    Ready

### SparkML
    Ready
