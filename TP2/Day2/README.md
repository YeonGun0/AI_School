# 🦁 TIL

## ✅ seaborn 시각화
> python0107
* `countplot` : 빈도수 비교할 때
* `unique`값이 엄청 많으면 `wordcloud` or 데이터 전처리 
* `hue`를 이용할 때 3개 이하의 색상 사용을 권장 for 시인성
* `df.nunique()`
* `series.unique()`


* `df.describe(include="object")`
  * 특정 데이터 타입을 출력하로 싶을 때 사용
* `df.describe(exclude="object")`
  * 특정 데이터 타입을 제외하고 싶을 때 사용


* `pd.crosstab(index=Series, columns=Series)`
* `df.unstack(), series.unstack()`
  * `MultiIndex`에서 `index`의 마지막 값을 `column`으로 끌어올림


* `pivot vs pivot_table`
  * `pivot` : 데이터 그대로 테이블로 출력
  * `pivot_table` : 데이터를 연산/가공하여 테이블로 출력
  ```python
    pd.pivot_table(data=df, index='origin', columns='cylinders', values='mpg')
  ```



* `boxplot`
* `boxenplot` : 수염에 해당하는 값도 box로 출력


* `scatterplot` : 점이 겹칠 수 있다는 단점
* `stripplot` : 점을 옆으로 찍어주지만 여전히 조금씩 겹침
* `swarmplot` : 점을 전혀 겹치지 않게 옆으로 찍음
* `countplot` : `x, y` 둘 중 하나만 입력 
* `catplot` : 기본값 = `stripplot`

<br>

## ✅ 웹 스크래핑, 크롤링
> python0201

## 🔗 Link
> * [FinanceData/FinanceDataReader: Financial data reader](https://github.com/FinanceData/FinanceDataReader)
> * [FinanceDataReader 사용자 안내서 | FinanceData](https://financedata.github.io/posts/finance-data-reader-users-guide.html)
> * https://pandas-datareader.readthedocs.io/en/latest/readers/index.html



* `HTTP`
* `requests`
* `finance-datareader`
* `fdr.StockListing()`


* `robot.txt`
  * 로봇 배제 표준
  * 웹 사이트에 로봇이 접근하는 것을 방지하기 위한 규약
  * 일반적으로 접근 제한에 대한 설명을 기술
  * 네이버 규약 조회 
  * `ex) naver.com/robots.txt`


* 한번에 많은 페이지를 요청하면 DDOS 공격으로 의심 받을 수 있음
* 일반적으로 `time.sleep()` 으로 시간 간격을 두고 가져옴


  

<br>

## ✅ 네이버 뉴스 웹 스크래핑
> python0202


* `html <table>` 태그는 `pandas, 엑셀`로 바로 가져올 수 있음



* 데이터 수집 방법
  * 수집하고자 하는 페이지의 `URL`을 알아본다.
  * 파이썬은 작은 브라우저 `requests` 를 통해 `URL`에 접근
  * `response.statue_code` 가 `200 OK` 라면 정상 응답
  * `request`의 `response` 값에서 `response.text` 만 받아옴
  * `html` 텍스트를 받아왔다면 `bs로 html 해석`
  * `soup.select` 를 통해 원하는 태그에 접근
  * 목록을 먼저 받아옴
  * 목록에서 행을 하나씩 가져옴
  * 행을 모아서 데이터프레임으로 만든다.
  > 판다스라면 `read_html`로 `table`로 된 태그에 대해 위 과정을 코드 한 줄로 가능


* `pd.concat()`
* `df.dropna()` : 결측치 제거하는 방법
* `~pd.Series([True, False])` == [False, True]
  * 앞에 `~`을 붙이면 반대로 출력
* 깊은 복사
  * `df2 = d1.copy()`
* 얕은 복사
  * `df2 = df1`


* `df_news.drop_duplicates()` : 중복 데이터 제거