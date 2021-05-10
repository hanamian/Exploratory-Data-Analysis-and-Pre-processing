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
untuk mengetahui seberapa kuat hubungan 2 kolom, apakah berkorelasi positif atau negatif. Berkorelasi kuat = multicollinearity
```python
dataset['BounceRates'].corr(dataset['Exit-Rates'])
dataset['TrafficType'].corr(dataset['Weekend'])
```
output:

![image](https://user-images.githubusercontent.com/49611937/117605523-19b3a300-b182-11eb-82ad-634ec971b946.png)
---
### 8. Distribusi Dataset
untuk melihat distribusi dataset.
```python
dataset['Revenue'].value_counts()
```
output:

![image](https://user-images.githubusercontent.com/49611937/117605422-d6593480-b181-11eb-89e5-8b6433f549a4.png)

---
