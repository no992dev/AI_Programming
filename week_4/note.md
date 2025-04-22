                  Underfitting        Overfitting  
What?             학습이 덜 됨         학습이 너무 많이 됨  
Why?              데이터부족->증대     노이즈 등등 학습  
                  모델 일반화 X->      모델이 지나치게 복잡->  
                  모델을 복잡하게       모델을 Simple하게  

fitting: 결혼식 웨딩드레스 피팅처럼 딱 맞추는 것

learning(학습): Data를 주어서 Rule을 습득하는 것

처음과 비교해서 교수님의 Rule을 습득함(ex. 깐깐함, 질문자주함 등..)  
Rule = Weight와 Bias를 구하는 일

모델의 일반화(Generalization): 어떤 데이터에서 테스트해도 동일한 결과가 나오도록  
ex) 미국에서 학습시킨 모델은 한국에서 좋은 결과가 나오지 않음

교재 159p
(a) Underfitting
(b) Best fit
(c) 노이즈까지 포함된 Overfitting

샘플링 편향: 훈련 데이터와 테스트 데이터가 동일하지 않음

정확도가 다른 이유:  
train/test data가 달라서  
data의 특성이 각각 다름  

Cross-Validation을 하는 이유: 공정한 결과를 얻어내기 위해서(data의 특성이 다 다름)

스케일링: 기준을 맞추는 것  
규제: Overfitting 방지  

회귀: X로부터 y의 상관관계 예측  
상관계수 R R^2  
혼공머신 120p

특성 공학(Feature Engineering)
혼공머신 150p

기존에 있는 Feature로부터 새로운 Feature를 만드는 것
새롭게 만든 Feature가 기존 Feature와 상관관계가 적을 때 도움이 됨(상관관계가 있으면 의미 X)

규제(Regularization)
혼공머신 158p
과적합을 방지하기 위한 기법
L1 L2
L1->중요 Feature 제외 나머지 없앰
L2->중요하지 않는 Feature의 가중치를 낮춤

Brute Force 방법 = 어떤 Feature를 선택할지 하나씩 다 해봄

불순도와 지니 계수

결정 트리
혼공머신 227p

앙상블
단점) 리소스 필요, 오래걸림

앙상블 기법의 하나인 RF
bootstrap->동일한 샘플을 중복하여 여러개 샘플을 만듦
12345 중에 뽑는 경우
1235
2234
4444 이런 식으로 뽑을 수도 잇음

KNN: 가까운넘
DT: 스무고개, 지니계수 중요
RF: 앙상블, 부트스트래핑
SVM:
LR: R^2

혼공머신 228p

부트스트랩
혼공머신 266p

회귀
교재 114p

정리
다음 시간에는 딥러닝
딥러닝 소스 예제가 AI-class에 breast cancer에 있음
원핫인코딩 하는 이유: 연관성을 끊기 위해서

과제
넘파이로 바꾸고 원핫인코딩
# input shape= 입력 feature의 개수
잘 만든 예제를 올리면 그걸 가지고 머신러닝 4가지, 딥러닝까지
