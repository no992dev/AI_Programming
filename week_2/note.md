1. 파일 불러오기
2. X, y로 나누기
3. train/test로 나누기  
4. 4가지 ML  
5. 평가  
-> 어떤 파일을 받든 기본적으로 해야 함

저장경로는 C:\\가 FM이고 /도 사용가능  
1주차 리포트에서 /usr/라고 써서 fail된 사례 많음(단순 복붙인 경우)

파일은 업로드뿐 아니라 URL로 옮겨올 수도 있다  
어떻게 하는지 모르면 지피티한테 물어봐라  
response = requests.get(url)

수업시간에 실습한 거 올릴 것

파일을 로드하는 방법 4가지  
1. 엑셀 파일/로컬 업로드
2. 엑셀 파일/웹 파일 로드
3. CSV 파일/로컬 업로드
4. CSV 파일/웹 파일 로드

train과 test, X와 y로 나누는 이유  
X는 레이블, y는 정답
X의 많은 feature로부터 y를 구하기 위해서  
train/test로 나누는 이유: 훈련한 모델을 테스트를 해봐야 하는데 훈련한 데이터로 나누면 의미없음

실습에 포함시킬 파일  
y_test와 y_pred 비교해보기(10개 정도)

train 데이터의 속성과 test 데이터의 속성이 같아야 성능이 좋다(모델의 일반화 Generalization)

제일 중요한 것은 기울기와 절편('추세'로 데이터를 나눔)

KNN 알고리즘은 지도학습이다    
레이블을 결정하는 게 목적  
주변에 가까운 k개의 점을 골라 판단  

ex) 점이 찍혔는데 '방어'로 판단하려면?  
주변에 가까운 점 3개를(k=3) 골라 판단(친구를 보면 그 사람을 알 수 있다)

붓꽃 알고리즘에 KNN 알고리즘을 적용해볼 것

깃허브에 정리할 거(사캠에 적어주심)  
csv, xls를 웹주소와 로컬 파일로 각각 읽어서(aka 4가지 방법) 데이터프레임 작성  
combined_dataset_1.xlsx랑 mobile.csv  
KNN 알고리즘 적용  
예측값과 정답 10개 정도 비교  
diabetes.csv 5가지 해보고 깃허브에 업로드


의료데이터에서 자주 발생하는 일로 imbalanced data(데이터가 한쪽으로 치우치는 현상)가 있음  

컬럼명 확인, 레이블.value_count

숫자를 다루는 dataframe과 numpy  
df의 특징: 보기 좋음, column들을 mainpulation할 수 있음  
numpy의 특징: 배열, 계산빠름

딥러닝할때는 numpy로 전환해줘야함  
머신러닝에서는 df랑 numpy 상관없음(혼공머신에서는 numpy)  
그러나 딥러닝은 numpy  


df manipulation

Exploring Data Analysis(웹사이트)

머신러닝의 레이블은 문자든 숫자든 상관없지만 딥러닝은 숫자여야 함

이름이 생존률에 영향을 주는가? NO  
-> 이름 레이블 drop  
성별(Sex)이 생존률에 영향을 주는가? YES  
나이(Age)가 생존률에 영향을 주는가? YES  
null 값(결측치)은 어떻게 하는가? 평균 나이로 매핑(fillna(mean_age) 함수)  
티켓(Ticket)이 영향? NO  
Fare(요금)이 영향? YES  
Pclass(1등석 2등석 3등석)? YES  
SibSp = 동승한 형제자매 수 YES  
Parch = 동승한 부모님 YES  
Cabin 필요없음 NO  
Embarked = 탑승창구 필요없음 NO

혼공머신 48p, 49p, 58p(전체 소스코드) 참조

먼저 익숙해진 다음에 원리를 배울 예정  
제일 중요한 것-> 자기가 스스로 해라
