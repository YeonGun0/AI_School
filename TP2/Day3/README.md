# 🦁 TIL

## ✅ 네이버 금융 개별종목 수집 with requests
> python0203

## 🔗 Link
> * [Requests: HTTP for Humans™ — Requests documentation](https://requests.readthedocs.io/en/master/)
> * [Quickstart — Requests documentation # custom-headers](https://requests.readthedocs.io/en/latest/user/quickstart/#custom-headers)
> * https://www.crummy.com/software/BeautifulSoup/bs4/doc/

* `Request URL` 데이터 찾기 : 개발자 도구 ➡️ JS ➡️ URL
  * `URL` 클릭하여 찾는 데이터가 맞는지 확인
  * 보통 `XHR, JS, Doc` 중 하나에서 데이터를 찾을 수 있음

### Http 메소드 종류
* 멱등성 : 수학이나 전산학에서 연산의 한 성질을 나타내는 것으로, 연산을 여러 번 적용하더라고 결과가 달라지지 않는 성질

| HTTP 메소드 |    RFC    | 요청에 Body가 있음 | 응답에 Body가 있음 | 안전  | 멱등(Idempotent) | 캐시 가능 |
|:--------:|:---------:|:------------:|:------------:|:---:|:--------------:|:-----:|
|   GET    | RFC 7231  |     아니오      |      예       |  예  |       예        |   예   |
|   HEAD   | RFC 7231  |     아니오      |     아니오      |  예  |       예        |      예       |
|   POST   | RFC 7231  |      예       |      예       | 아니오 |      아니오       |예|
|   PUT    | RFC 7231  |      예       |      예       |     아니오      |  예  |      아니오       |
|  DELETE  | RFC 7231  |     아니오      |      예       | 아니오 |예|     아니오      |
| CONNECT  | RFC 7231  |      예       |      예       | 아니오 |      아니오       |     아니오      |
| OPTIONS  | RFC 7231  |     선택사항     |      예       |  예  |       예        |     아니오      |
|  TRACE   | RFC 7231  |     아니오      |      예       |  예  |       예        |     아니오      |
|  PATCH   | RFC 5789  |      예       |      예       | 아니오 |      아니오       |      예       |

### Http 상태코드
* `1xx` (정보): 요청을 받았으며 프로세스를 계속
* `2xx` (성공): 요청을 성공적으로 받았으며 인식했고 수용
* `3xx` (리다이렉션): 요청 완료를 위해 추가 작업 조치가 필요
* `4xx` (클라이언트 오류): 요청의 문법이 잘못되었거나 요청을 처리할 수 없음
* `5xx` (서버 오류): 서버가 명백히 유효한 요청에 대해 충족을 실패 





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


* `df.reset_index(drop=True)`
* `df.to_csv(index=False)`
* `trange`
* `requests`
* `GET`
* `POST`
* `headers`
* `BeautifulSoup`
* `bs.select("tag")`
* `bs.find_all("tag")`


<br>

## ✅ ETF 스크래핑 with JSON
> python0204

## 🔗 Link
> * 출처 : [JSON - 위키백과, 우리 모두의 백과사전](https://ko.wikipedia.org/wiki/JSON)


* `json`
* `response.json()`
* `requests.get(url)`
* `pd.read_csv(file_name, dtype={"col":"type"})`
  * `col`에 `type` 지정 
* `df["new_col"] = df["col1"].str.split(expand=True)`
  * `expand=True` : 리스트로 반환되는 `split()` 값을 데이터프레임으로 반환
```python
from datetime import datetime

today = datetime.today().strftime("%Y-%m%d")
```