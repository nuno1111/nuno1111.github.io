## 텍스트 마이닝
- Text 데이터의 형태소 분석을 통한 분석
- KoNLP
- Wordcloud

### R
    char_list <- c('이번 예제는 텍스트 분석에서 많이 사용되는 tm 패키지와 KoNLP 패키지를 사용해서 나온 결과'
                   ,'비교해서 보여 드리겠습니다. 예제로 사용할 파일은 국내 유명 호텔 중 2 곳을 이용한 고객들'
                   ,'이용 후기를 모은 파일입니다. 이미 앞에서 KoNLP 패키지와 tm 패키지 설명은 다 했기 때문'
                   ,'내용이 중복되어 여기서는 결과 화면과 소스 코드만 보여 드리겠습니다')
    library(KoNLP)
    library(tm)
    ko.corpus <- Corpus(VectorSource(char_list)) # Corpus생성
    inspect(ko.corpus[1:3]) # 코퍼스탐색
    ko.corpus[[1]]$content

    # 데이터 전처리
    ko.corpus <- tm_map(ko.corpus, stripWhitespace) # 기본 Transformation 함수 : 빈공간(\n) 제거
    ko.corpus <- tm_map(ko.corpus, content_transformer(gsub), pattern='@\\S*', replacement='') # @뒤 단어제거
    ko.corpus <- tm_map(ko.corpus, content_transformer(gsub), pattern='http\\S*', replacement='') # http로 시작되는 URL 제거
    ko.corpus <- tm_map(ko.corpus, removePunctuation) # 문장 부호 및 구두점 제거
    ko.corpus <- tm_map(ko.corpus, content_transformer(tolower)) # 소문자로 일괄변경

    mystopword <- c('해서','드리겠습니') # 영어는 stopwords('en')
    ko.corpus <- tm_map(ko.corpus, removeWords, mystopword) # 단어지정 제거

    ko.corpus.m <- tm_map(ko.corpus, extractNoun) # 명사추출

    # TDM 생성
    ko.TDM <- TermDocumentMatrix(ko.corpus.m)  

    # 빈도 계산
    ko.TDM.m <- as.matrix(ko.TDM)
    term.freq <- sort(rowSums(ko.TDM.m), decreasing = T)
    barplot(head(term.freq,10)) # 빈도 top 10

    library(wordcloud)
    wordcloud(words=names(term.freq)
              , freq = term.freq
              , min.freq = 1
              , random.order = F
              , random.color = T
              , colors = brewer.pal(8,'Dark2')
    )



### Python
    Ready

### SparkML
    Ready
