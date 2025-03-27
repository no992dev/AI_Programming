## 머신러닝 라이브러리 임포트
```
import pandas as pd
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.preprocessing import LabelEncoder, StandardScaler
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.svm import SVC
from sklearn.linear_model import LogisticRegression
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, confusion_matrix
import random
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
