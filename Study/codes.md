## 주요 항목
* [머신러닝 라이브러리 임포트](#머신러닝-라이브러리-임포트)
* [데이터 로드](#로컬-데이터-로드)
* [전처리](#결측치-확인)
* [Train Test 분리](#Train-Data와-Test-Data-분리)
* [머신러닝 모델 4종](#Decision-Tree)
* [수동 정확도 비교](#수동으로-예측값과-정답-비교)
* [One-Hot Encoding](#One-Hot-Encoding)
<br><br>
## 머신러닝 라이브러리 임포트
```
import pandas as pd
from sklearn.model_selection import train_test_split, cross_val_score, confusion_matrix
from sklearn.preprocessing import LabelEncoder, StandardScaler
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.svm import SVC
from sklearn.linear_model import LogisticRegression
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, confusion_matrix
```
## 로컬 데이터 로드
```
df = pd.read_csv("C:/AI_Dataset/.csv")
df.head()
```
## 웹 데이터 로드
```
df = pd.read_csv("https://github.com/MyungKyuYi/AI-class/raw/main/.csv")
print(csv_web_df.head())
```
## Columns 확인
```
df.columns
```
## 데이터의 count 확인(imbalanced data 등 확인에 사용)
```
print(df['label'].value_counts())
```
## 결측치 확인
```
df.isnull().sum()
```
## 결측치 제거(평균치로 채우는 경우)
```
mean_value = df['Age'].mean()
df['Age'] = df['Age'].fillna(mean_value)
print(df.isnull().sum()) # 결측치 다시 체크
```
## 결측치 제거 또는 필요없는 열 드롭
```
# 열 하나만 드롭할 경우
# axis = 1은 열(column)을 삭제한다는 뜻, 행을 삭제할 경우 axis = 0)
df = df.drop('label', axis = 1)
df.head()
```
```
# 열 여러 개를 드롭할 경우
drop_columns = ["Name", "Ticket", "Cabin", "Embarked"]
df = df.drop(columns = drop_columns)
print(df.head())
```
## Label Encoding
```
encoder = LabelEncoder()
df['Sex'] = encoder.fit_transform(df['Sex'])
print(df.head())
```
## Train Data와 Test Data 분리
```
X = df.drop(columns=['Survived'])
y = df['Survived']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```
## Train 데이터와 Test 데이터 스케일링(StandardScaler)
```
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```
## Decision Tree
[맨 위로](#주요-항목)  
scaled data를 사용하려면 X_train과 X_test 대신 X_train_scaled와 X_test_scaled를 사용하면 됨
```
# DT 모델 학습
dt_model = DecisionTreeClassifier(random_state=42)
dt_model.fit(X_train, y_train)

# 예측 및 평가
y_pred = dt_model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
cross_val_acc = cross_val_score(dt_model, X, y, cv=5).mean() # 교차 검증
cm = confusion_matrix(y_test, y_pred)
print(f"Decision Tree Accuracy: {accuracy:.4f}")
print(f"Cross-Validation Accuracy: {cross_val_acc:.4f}")
print(f"Confusion Matrix:\n{cm}\n")
```
## Random Forest
```
# RF 모델 학습
rf_model = RandomForestClassifier(n_estimators=100, random_state=42)
rf_model.fit(X_train, y_train)

# 예측 및 평가
y_pred = rf_model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
cross_val_acc = cross_val_score(rf_model, X, y, cv=5).mean()
cm = confusion_matrix(y_test, y_pred)
print(f"Random Forest Accuracy: {accuracy:.4f}")
print(f"Cross-Validation Accuracy: {cross_val_acc:.4f}")
print(f"Confusion Matrix:\n{cm}\n")
```
## Support Vector Machine
```
# SVM 모델 학습
svm_model = SVC()
svm_model.fit(X_train, y_train)

# 예측 및 평가
y_pred = svm_model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
cross_val_acc = cross_val_score(svm_model, X, y, cv=5).mean()
cm = confusion_matrix(y_test, y_pred)
print(f"Support Vector Machine Accuracy: {accuracy:.4f}")
print(f"Cross-Validation Accuracy: {cross_val_acc:.4f}")
print(f"Confusion Matrix:\n{cm}\n")
```
## Logistic Regression
```
# LR 모델 학습
lr_model = LogisticRegression(max_iter=200)
lr_model.fit(X_train, y_train)

# 예측 및 평가
y_pred = svm_model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
cross_val_acc = cross_val_score(lr_model, X, y, cv=5).mean()
cm = confusion_matrix(y_test, y_pred)
print(f"Logistic Regression Accuracy: {accuracy:.4f}")
print(f"Cross-Validation Accuracy: {cross_val_acc:.4f}")
print(f"Confusion Matrix:\n{cm}\n")
```
## K-Nearest Neighbors
```
# KNN 모델 학습 (k=3 사용)
k = 3
knn_model = KNeighborsClassifier(n_neighbors=k)
knn_model.fit(X_train, y_train)

# 예측 및 평가
y_pred = knn_model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
cross_val_acc = cross_val_score(knn_model, X, y, cv=5).mean()
cm = confusion_matrix(y_test, y_pred)
print(f'K-Nearest Neighbors Accuracy: {accuracy:.4f}')
print(f"Cross-Validation Accuracy: {cross_val_acc:.4f}")
print(f"Confusion Matrix:\n{cm}\n")
```
## 수동으로 예측값과 정답 비교
```
# 예측값과 정답 비교

# 테스트 데이터에서 10개 샘플 선택
X_sample = X_test[:10]
y_sample_true = y_test.iloc[:10]

# 모델 선택 (예: Random Forest)
model = RandomForestClassifier()
model.fit(X_train, y_train)
y_sample_pred = model.predict(X_sample)

# 결과 비교
comparison = pd.DataFrame({
    "Actual": y_sample_true.values,
    "Predicted": y_sample_pred
})
comparison["Result"] = comparison["Actual"] == comparison["Predicted"]

print(comparison)
```
## One-Hot Encoding
```
X = X.values
Y = pd.get_dummies(y).values
X[:5] # X.head()와 유사
Y[:5] # Y.head()와 유사
```
## One-Hot Encoding된 데이터 Train Data와 Test Data로 분리
```
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 42)
```
<sub>딥러닝 소스는 나중에</sub>
