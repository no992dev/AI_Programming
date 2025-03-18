마지막으로 Step by Step으로 머신러닝 실습 진행

car_evaluation.csv <- archive.zip

구글 코랩 사용법도 배움  
코랩을 쓰는 이유?  
H4 같은 (고급) GPU를 사용할 수 있기 때문  
그러나 코랩 환경에서는 에러가 많아 GPU 사용을 권장하지 않음  
수업중 한 번만 해보고 하지 않음

코랩의 장점  
1. GPU

코랩 사용방법  
1. 구글 드라이브에 업로드해야 함  
여기서 코랩 생성  
2. 런타임 GPU로 변경(필수 X)  
3. 폴더 마운트  
`content/drive/MyDrive` 폴더 안에 내 드라이브 파일이 있음  

`index_col = 0` -> 인덱스 등의 garbage data 제거용  
`header = None` -> column명을 0 1 2 3 4 5 6으로 변경

column명 변경법  
`df.columns = ['price', 'maint', 'doors', 'persons', 'lug_boot', 'safety', 'class']`

->레이블 확인 ☆  
->결측치 확인 ☆  
->인코딩(머신러닝은 사실 필요없음)  

numpy는 배열 형식이고 속도 빠름(수치형)  
dataframe은 엑셀 형식이고 보기 좋음

그래서 dataframe으로 작업하고 최종 분류를 numpy로 함

Scaler의 역할  
값을 일괄적으로 축소시키는? 역할(왜 그러는지는 추후 설명)  
예시) 나이가 20세인 사람을 0.2로 축소  
StandardScaler는 0과 1 사이 값으로 축소  

되도록 한 덩어리로 묶지 말고 나눠서 코딩

예시1  
[[ 73   4   6   0]  
 [  4   7   0   0]  
 [ 12   0 223   0]  
 [  2   0   0  15]]  
confusion matrix의 의미  
위에서부터  
0 예측-0 정답, 0 예측-1 오답, 0 예측-2 오답, ..  
1 예측-0 오답, 1 예측-1 정답, ...  
2 예측-0 오답, 2 예측-1 오답, 2 예측-2 정답
...  
즉 (0, 0), (1, 1), (2, 2), (3, 3)이 정답을 맞힌 값  

예시 2  
```
Standing  
Sitting          ☆  
Laying  
              Standing       Sitting         Laying
```
☆표시는 Sitting이라고 예측했으나 Standing인 경우


우리가 배울 수 있는 '지능'은 분류와 회귀 2종류밖에 없음  
회귀 vs 분류?

분류 | 회귀  
**이산적인 값 | 연속적인 값(중요)**  
API가 다름  
Binary Clsf 등 | MSE(Mean-Square Error)  

ex) 나이는 이산적인 값이지만, 연속적인 값이기도 함(1살~100살)  
그럼 나이는 이산? 연속?  
성별(남성, 여성)은 순서가 없음  
1학년, 2학년, 3학년, 4학년은 순서가 있음(학년은 큰 의미는 없음)  
즉 순서가 의미가 있나가 중요(연관성이 있느냐)  
즉 나이는 연속적인 의미가 있기에 회귀(Regression)  

001  
010  
100  
이렇게 인코딩(연속적인 값이 없음을 의미함)  
one-hot encoding

ML_regression_boston.ipynb

X_train.shape  
테스트 샘플 16000개, column 8개 라는 뜻

Regression은 값을 맞히는 게 의미가 없기 때문에 Mean Square Error(평균제곱근오차)를 구함

diabetes.csv  
outcome을 classification하는 대신 BMI를 regression(실습)  

중요한 정보(핵심 정보)만 이용하는 것이 성공률이 더 좋을 수도 있음  
**이를 Feature Selection ☆이라고 부름**  
예시) 어중이떠중이를 많이 데려가기보다 특수부대 몇명 데려가는 것이 기습에 효과적임  

PRICE와 다른 column의 관계를 볼려면 히트맵에서 제일 오른쪽 줄 PRICE 줄만 보면 된다  

산점도  
x값 = PRICE  
y값 = MedInc  

산점도에서 눈에 보기에도 가까운 게 실제로 평균제곱근오차가 낮다

https://hongong.hanbit.co.kr/%ED%98%BC%EC%9E%90-%EA%B3%B5%EB%B6%80%ED%95%98%EB%8A%94-%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D-%EB%94%A5%EB%9F%AC%EB%8B%9D/ 혼자 공부하는 머신러닝+딥러닝

major class, minor class  
major 쪽에 치우치는 경향->데이터 편향

예시) 대선 여론조사  
여론조사는 A 후보가 될 것으로 예측했으나 B 후보가 당선됨  
데이터 편향이 생김(혼공머신 72p)  
imbalanced data  

AI의 4가지 단계  
Data Collection 데이터 수집  
Preprocessing 전처리(성능을 좋게 만들게 하기 위해 하는 모든 처리, 결측치, 스케일링 등을 말함)  
Training 학습  
Scoring 평가  

데이터 전처리(혼공머신 95p 참조)  
빙어에 더 가까움에도 그래프 눈속임(?) 때문에 도미에 가깝다고 판단  
**<ins>스케일링을 하는 이유</ins>**  
(StandardScaler의 경우) 0~1 사이로 맞춰서 눈속임을 없애기 위함  
혼공머신 99p 참조


정리
1. 머신러닝 실습 이제 안함(그러나 불시에 실습 시험 봄, 성적에 반영됨)
