# 🦁 TIL
### ✅ 왜 엑셀이 아닌 파이썬을 사용하는가?
> * 엑셀을 이용하여 데이터 분석뿐만 아니라 딥러닝 모델 구현도 가능
> * 그러나 100만 줄 이상, 1GB 이상의 파일은 엑셀에서 상당히 느리거나 열리지 않음
> * 다양한 **라이브러리**와 **커뮤니티**

<br>

### ✅ ETL vs ELT
#### ➡️`ETL`❓
> `Extract`, `Transform`, `Load`의 앞글자를 딴 용어 <br>
> 여러가지 데이터 소스에서 추출`(Extract)`하고, <br>
> 데이터를 원하는 형태로 변형`(Transform)`하고, <br>
> `DW`로 적재`(Load)`하는 과정

> 즉, 데이터 소스에서 가져온 `raw data`로 데이터 웨어하우스에 바로 저장할 수 없으니 `ETL`과정이 필요 <br>
> 비즈니스 또는 분석용도에 맞춰 데이터를 잘 정제해야 함
> 데이터 크기가 커질수록 `Transform`에 많은 시간 소요

#### ➡️`ELT`❓
> 요즘에는 `ETL`에서 `ELT`방식으로 흐름이 바뀌고 있음 <br>
> 데이터를 추출`(Extract)`하고, 적재`(Load)`를 먼저 하고, 변형`(Transform)`하는 것 <br>
> 모든 데이터 소스를 하나의 공간으로 적재한 뒤, 그 용도에 따라서 필요한 경우 툴이나 시스템이 직접 변형하게 하는 과정

#### ➡️`ETL` 에서 `ELT` 로
> 대량의 데이터 발생 <br>
> `ETL`방식은 데이터가 커질수록 `Transform`하는데 시간이 걸림 <br>
> 그런데 점점 데이터가 많아지다보니 `ETL`에 한계 발생 <br>
> `우선 데이터를 다 저장하고, 이 데이터를 어떻게 쓸지는 나중에 고민하자` <br>
> 마치 호수처럼 데이터 웨어하우스 앞단에 모든 데이터를 다 저장해두고 `(Data Lake)` <br>
> 그 중 일부만 용도에 따라 데이터 웨어하우스로 가져가서 쓰자는 컨셉

