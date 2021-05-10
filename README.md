# Exploratory Data Analysis and Pre-processing

### 1. Dimensi dataset
```python
dataset.shape
```
output:
```
Shape dataset: (12330, 18)
```
---
### 2. 5 Data Teratas
```python
dataset.head()
```
output:

![image](https://user-images.githubusercontent.com/49611937/117600168-a441d580-b175-11eb-941b-12f8af0f43de.png)

---
### 3. 5 Data Terbawah
```python
dataset.tail()
```
output:

![image](https://user-images.githubusercontent.com/49611937/117600548-54174300-b176-11eb-94aa-97ed87607062.png)

---
### 4. Info
```python
dataset.info()
```
output:

![image](https://user-images.githubusercontent.com/49611937/117600758-c556f600-b176-11eb-914e-70b05981fc7c.png)

---
### 5. Deskripsi Statistik
```python
dataset.describe()
```
output:

![image](https://user-images.githubusercontent.com/49611937/117600805-e15a9780-b176-11eb-884d-b30c805667a3.png)

---
### 6. Correlation
untuk mengetahui seberapa kuat hubungan antar feature
```python
dataset.corr()
```
output:

![image](https://user-images.githubusercontent.com/49611937/117604814-89289300-b180-11eb-94cb-946d1ddaad78.png)

---
### 7. Correlation antar 2 kolom
Bisa menggunakan **corr** langsung atau memakai **loc**
untuk mengetahui seberapa kuat hubungan 2 kolom, apakah berkorelasi positif atau negatif. Berkorelasi kuat = multicollinearity
```python
dataset['BounceRates'].corr(dataset['Exit-Rates'])
dataset['TrafficType'].corr(dataset['Weekend'])

#atau
dataset_corr = dataset.corr()
dataset_corr.loc['BounceRates', 'Exit-Rates']
dataset_corr.loc['TrafficType', 'Weekend']
```
output:

![image](https://user-images.githubusercontent.com/49611937/117605523-19b3a300-b182-11eb-82ad-634ec971b946.png)
---
### 8. Distribusi Dataset
untuk melihat distribusi dataset. Kalau tidak seimbang = **Imbalanced**
```python
dataset['Revenue'].value_counts()
```
output:

![image](https://user-images.githubusercontent.com/49611937/117605422-d6593480-b181-11eb-89e5-8b6433f549a4.png)

---
### 9. Missing Value
```python
dataset.isnull()
dataset.isnull().sum()
dataset.isnull().any()
dataset.isnull().any().sum()

#Total missing value
dataset.isnull().sum().sum()
```
Result:

![image](https://user-images.githubusercontent.com/49611937/117626829-bafe2180-b1a1-11eb-988a-8de19e9344dc.png)
![image](https://user-images.githubusercontent.com/49611937/117627069-fe589000-b1a1-11eb-864e-a6a2c7aecb32.png)
![image](https://user-images.githubusercontent.com/49611937/117621973-555b6680-b19c-11eb-8de6-9564d0211136.png)
```
8
12
```

---
### 10. Drop Misssing Value
```python
dataset.dropna()
```
---
### 11. Fill missing value using MEAN, MEDIAN
```python
dataset.fillna(dataset.mean(), inplace=True)
dataset.fillna(dataset.median(). inplace=True)
```
---
### 12. Data Scaling
Scaling diperlukan jika range data setiap feature tidak seragam. Misal feature A = 1-1000, feature B = 0-1. Tujuannya adalah **agar tidak ada dominasi saat training dan model yang dihasilkan tidak bias**. Kita bisa membuat data menjadi ber-rentang 0-1 dengan *sklearn.preprocessing* **.MinMaxScaler()**. Rumusnya adalah:

![image](https://user-images.githubusercontent.com/49611937/117653835-1e4a7c80-b1bf-11eb-8eba-14a6614b242b.png)

```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler

#Kolom yang mau discale
scaling_column = ['Administrative','Administrative_Duration','Informational','Informational_Duration','ProductRelated','ProductRelated_Duration','BounceRates','ExitRates','PageValues']

#Apply fit_transform
dataset[scaling_column] = scaler.fit_tranform(dataset[scaling_column])

print(dataset[scaling_column].describe().T[['min','max']])
```
Result:

![image](https://user-images.githubusercontent.com/49611937/117660096-ef380900-b1c6-11eb-8dcd-13d59c8a5e89.png)

---
### 13. Konversi Tipe data Objek ke Numerik (int atau float)
Bisa menggunakan *sklearn.preprocessing* **LabelEncoder**
```python
import numpy as np
from sklearn.preprocessing import LabelEncoder

# Convert feature 'Month'
LE = LabelEncoder()
dataset['Month'] = LE.fit_transform(dataset['Month'])
print(LE.classes_)
print(np.sort(dataset['Month'].unique()))				
print('')

# Convert feature'VisitorType'
LE = LabelEncoder()
dataset['VisitorType'] = LE.fit_transform(dataset['VisitorType'])
print(LE.classes_)
print(np.sort(dataset['VisitorType'].unique()))
```
![image](https://user-images.githubusercontent.com/49611937/117662283-95850e00-b1c9-11eb-8c4e-f5ca361337b4.png)
