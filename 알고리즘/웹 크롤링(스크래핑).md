

# 웹 크롤링(스크래핑)



```R
url_tvcast <- "http://tvcast.naver.com/jtbc.youth"
html_tvcast <- read_html(url_tvcast,encoding = "UTF-8")
#url에서 html 파일 읽어오고 저장한다.
```

* `html_node()` : 매칭되는 한 요소만 반환
* `html_nodes() `: 모든 요소 반환

```r
html_tvcast %>% html_nodes(".title a")
# class가 title인 부분에서 a태그에 해당하는 내용 추출
html_tvcast %>% html_nodes(".title a") %>% html_text()
# 텍스트만 추출
tvcast_df <- html_tvcast %>% html_nodes(".title a") %>% html_text() %>% data.frame()

```

