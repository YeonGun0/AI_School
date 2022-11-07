# 🦁 TIL


## ✅ Regression

### - 오차 측정 방법

#### MAE(Mean Absolute Error)
* 예측값과 실제값의 차이에 대한 절댓값의 평균
* 대회에서 사용하는 경우는 많지 않음, 아래 방법들을 이해하기 위함

#### MAPE(Mean Absolute Percentage Error)
* (실제값 - 예측값 / 실제값)의 절댓값에 대한 평균
* 0에 가까울수록 좋은 값

#### MSE(Mean Squared Error)
* 실제값 - 예측값의 차이의 제곱의 평균
* MAE와 비슷해 보이나 제곱을 통해 음수를 양수로 변환
* 분산과 유사한 공식
  * 분산 : 평균으로부터 얼마나 떨어져 있는지 확인
  * MSE : 실제값으로부터 얼마나 떨어져 있는지 확인

#### RMSE(Root Mean Squared Error)
* MSE의 제곱근
* 표준편차와 유사한 공식

> 상황에 따라 어떤 방법이 좋을지 판단해야 함
> * A : 100억 부동산 110억으로 예측
> * B : 1억 부동산 2억으로 예측
> * MAE로 평가하면 B가 더 잘 예측
> * MAPE로 평가하면 A가 더 잘 예측 <br>
> MSE가 절댓값에 비해 오차가 더 큰 값에 대해 패널티를 더 많이 줄 수는 있지만 예측 비율에 대해서는 파악할 수 없음

<br>

### - train_test_split
* `stratify`
  * `train set`과 `test set`를 분리할 때, `class` 비율을 동일하게 하는 것
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, stratify=y, random_state=42)
```


<br>

### - plt.subplots()
* 여러 그래프를 한 곳에 그리기
```python
plt.subplots(nrows=2, ncols=4, figsize=(12, 7))
# 출력물이 아래와 같음, tuple 형태
# (<Figure size 1200x700 with 8 Axes>,
#  array([[<AxesSubplot:>, <AxesSubplot:>, <AxesSubplot:>, <AxesSubplot:>],
#         [<AxesSubplot:>, <AxesSubplot:>, <AxesSubplot:>, <AxesSubplot:>]],
#        dtype=object))

# figure size를 fig
# array를 axes에 지정
fig, axes = plt.subplots(nrows=2, ncols=4, figsize=(12, 7))

# 파라미터 ax를 이용하여 subplot의 위치 지정
# set_title : title of subplot
sns.countplot(data=df, x=y_train, ax=axes[0, 1]).set_title("train")
sns.countplot(data=df, x=y_test, ax=axes[1, 3]).set_title("test")
```

<br>

## ✅ hyper parameter tuning
* 하이퍼 파라미터 최적화
  * 알고리즘의 하이퍼 파라미터 값을 지정하고 지정 된 값 중 좋은 성능을 내는 파라미터를 찾는 과정
* `GridSearchCV`
  * [GridSearchCV 공식 문서](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html#sklearn.model_selection.GridSearchCV) 
  * 지정 된 구간에 대한 값에 대해서 탐색
  * 조합의 수 만큼 실행
* `RandomizedSearchCV`
  * [RandomizedSearchCV 공식 문서](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html#sklearn.model_selection.RandomizedSearchCV) 
  * 지정 된 구간 외에 최적 값이 있을 때 그리드 서치로 찾지 못하는 단점을 보완
  * 랜덤한 값들을 지정하여 성능을 평가하고 가장 좋은 성능을 내는 파라미터를 찾음
  * 좋은 성능을 내는 구간으로 점점 좁혀가며 파라미터 탐색
  * `k-fold` * `n_iter` 만큼 실행

|  -  |                               GridSearchCV                               |                                 RandomizedSearchCV                                 |
|:---:|:------------------------------------------------------------------------:|:----------------------------------------------------------------------------------:| 
| 정의  |                하이퍼 파라미터 후보군 들을 <br/> 완전 탐색하여 하이퍼 파라미터를 검색                |   정해진 횟수 안에서 정의된 하이퍼 파라미터<br/>후보군들로부터의 조합을 랜덤하게 샘플링하여<br/>최소의 오차를 갖는 하이퍼 파라미터 검색   |
| 장점  | 검증하고 싶은 하이퍼 파라미터 수치를<br/> 지정하면 수치별 조합을 모두 검증하여 <br/> 최적의 파라미터 검색의 정확도 향상 |                무작위로 값을 선정하고 그 조합을 검증하므로<br/>빠른 속도로 최적의 파라미터 조합을 검색                 |
| 단점  |    후보군의 개수가 많으면 많을수록 <br/> 기하급수적으로 찾는 시간은 오래 걸리며 <br/>후보군들을 정확히 설정 필요 <br/> 지정된 조합만 보기 때문에 해당 그리드를 <br/> 벗어나는 곳에 최적의 하이퍼 파라미터가 <br/> 있다면 찾지 못함  | 후보군을 신중히 결정해야하며, 랜덤한 조합들 중 <br/>최적의 하이퍼 파라미터를 찾는다는 보장이 없음<br/>횟수를 늘려주면 시간도 비례하여 증가 |

