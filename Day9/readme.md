# Day9




## 1. Your First Machine Learning Model

모델을 정의하고 학습시키기 전에 학습시킬 데이터를 먼저 준비해야 한다. 
데이터를 가져오는 일은 앞에서 배운 pandas를 이용하도록 한다. 


```python
import pandas as pd
from sklearn.tree import DecisionTreeRegressor

data_path = "../data/melb_data.csv"
home_data = pd.read_csv(data_path)
home_data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Suburb</th>
      <th>Address</th>
      <th>Rooms</th>
      <th>Type</th>
      <th>Price</th>
      <th>Method</th>
      <th>SellerG</th>
      <th>Date</th>
      <th>Distance</th>
      <th>Postcode</th>
      <th>...</th>
      <th>Bathroom</th>
      <th>Car</th>
      <th>Landsize</th>
      <th>BuildingArea</th>
      <th>YearBuilt</th>
      <th>CouncilArea</th>
      <th>Lattitude</th>
      <th>Longtitude</th>
      <th>Regionname</th>
      <th>Propertycount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Abbotsford</td>
      <td>85 Turner St</td>
      <td>2</td>
      <td>h</td>
      <td>1480000.0</td>
      <td>S</td>
      <td>Biggin</td>
      <td>3/12/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>202.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Yarra</td>
      <td>-37.7996</td>
      <td>144.9984</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Abbotsford</td>
      <td>25 Bloomburg St</td>
      <td>2</td>
      <td>h</td>
      <td>1035000.0</td>
      <td>S</td>
      <td>Biggin</td>
      <td>4/02/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>156.0</td>
      <td>79.0</td>
      <td>1900.0</td>
      <td>Yarra</td>
      <td>-37.8079</td>
      <td>144.9934</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Abbotsford</td>
      <td>5 Charles St</td>
      <td>3</td>
      <td>h</td>
      <td>1465000.0</td>
      <td>SP</td>
      <td>Biggin</td>
      <td>4/03/2017</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>134.0</td>
      <td>150.0</td>
      <td>1900.0</td>
      <td>Yarra</td>
      <td>-37.8093</td>
      <td>144.9944</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abbotsford</td>
      <td>40 Federation La</td>
      <td>3</td>
      <td>h</td>
      <td>850000.0</td>
      <td>PI</td>
      <td>Biggin</td>
      <td>4/03/2017</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>94.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Yarra</td>
      <td>-37.7969</td>
      <td>144.9969</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Abbotsford</td>
      <td>55a Park St</td>
      <td>4</td>
      <td>h</td>
      <td>1600000.0</td>
      <td>VB</td>
      <td>Nelson</td>
      <td>4/06/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>120.0</td>
      <td>142.0</td>
      <td>2014.0</td>
      <td>Yarra</td>
      <td>-37.8072</td>
      <td>144.9941</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>



pandas를 통해 가져온 데이터를 우리가 학습시키길 원하는 형태로 변환시켜야 한다. 
에를 들면 특정 열만 가져와서 학습에 참고하도록 한다거나 train dataset과 test dataset을 분리하는 작업을 하여야 한다.
또한 추가적으로 정규화나 이상치 제거와 같은 전처리도 진행해 주어야 하지만 여기서는 간단히만 알아본다. 



```python
y=home_data.Price
x.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Rooms</th>
      <th>Distance</th>
      <th>Postcode</th>
      <th>Bedroom2</th>
      <th>Bathroom</th>
      <th>Car</th>
      <th>Landsize</th>
      <th>Lattitude</th>
      <th>Longtitude</th>
      <th>Propertycount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>202.0</td>
      <td>-37.7996</td>
      <td>144.9984</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>156.0</td>
      <td>-37.8079</td>
      <td>144.9934</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>134.0</td>
      <td>-37.8093</td>
      <td>144.9944</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>94.0</td>
      <td>-37.7969</td>
      <td>144.9969</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>120.0</td>
      <td>-37.8072</td>
      <td>144.9941</td>
      <td>4019.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
x=x.select_dtypes(include=['int64','float64'])
```


```python
x=x.drop(columns=['Car'],axis=1)
x.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Rooms</th>
      <th>Distance</th>
      <th>Postcode</th>
      <th>Bedroom2</th>
      <th>Bathroom</th>
      <th>Landsize</th>
      <th>Lattitude</th>
      <th>Longtitude</th>
      <th>Propertycount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>202.0</td>
      <td>-37.7996</td>
      <td>144.9984</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>156.0</td>
      <td>-37.8079</td>
      <td>144.9934</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>134.0</td>
      <td>-37.8093</td>
      <td>144.9944</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>94.0</td>
      <td>-37.7969</td>
      <td>144.9969</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>120.0</td>
      <td>-37.8072</td>
      <td>144.9941</td>
      <td>4019.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
x.isna().sum()
```




    Rooms            0
    Distance         0
    Postcode         0
    Bedroom2         0
    Bathroom         0
    Landsize         0
    Lattitude        0
    Longtitude       0
    Propertycount    0
    dtype: int64




```python
iowa_model = DecisionTreeRegressor(random_state=1)
```


```python
iowa_model.fit(x,y)
```




    DecisionTreeRegressor(random_state=1)




```python
predictions=iowa_model.predict(x)
print(predictions[:5])
print(y[:5])
```

    [1480000. 1035000. 1465000.  850000. 1600000.]
    0    1480000.0
    1    1035000.0
    2    1465000.0
    3     850000.0
    4    1600000.0
    Name: Price, dtype: float64


## 2. Model Validation

앞서 우리는 모델을 정의하고 그 모델에 불러온 데이터를 학습시켜 결과를 반환하였다. 
하지만 앞에서 한 예제는 문제점이 있다. 바로 학습에 대한 평가(validation)또한 학습데이터로 진행했다는 점이다.
학습데이터로 평가까지 진행한다면 그 모델은 오직 학습데이터에만 잘 작동하는 모델이 될 것이다. 
모델은 범용성을 확보해야 하는 것이 중요하다. 따라서 이러한 범용성을 가지는지 평가하기 위해서는 
모델이 처음보는 데이터(학습에 사용하지 않은 데이터)로 평가를 실행해야 한다.

여기서 이 문제를 해결하기 위헤 train dataset을 train, validation dataset으로 나눈다. 



```python
from sklearn.model_selection import train_test_split

train_x,val_x,train_y,val_y = train_test_split(x,y,random_state=1)
```


```python
print(len(train_x),len(val_x),len(train_y),len(val_y))
```

    10185 3395 10185 3395


위와 같이 ```train_tset_split()```메소드를 이용하여 성공적으로 train,val데이터셋을 분리하였다. 

이렇게 나눈 dataset을 이용하여 다시 새로운 모델에 학습을 시킨다. 



```python
iowa_model = DecisionTreeRegressor(random_state=1)
iowa_model.fit(train_x,train_y)
```




    DecisionTreeRegressor(random_state=1)




```python
predictions=iowa_model.predict(val_x)
print(predictions[:5])
print(val_y[:5])
```

    [1100000. 1105000. 2275000.  900000. 3150000.]
    321      1640000.0
    4003      675000.0
    13348    2800000.0
    2697      615000.0
    12600    2700000.0
    Name: Price, dtype: float64


결과를 보니 예측값과 실제값의 차이가 꽤 크다. 
이를 mae(mean absolute error)라는 metrics를 사용하여 평가해 보자.


```python
from sklearn.metrics import mean_absolute_error

val_mae = mean_absolute_error(val_y,predictions)
print(val_mae)
```

    234689.40805105548


결과를 보면 꽤 큰 숫자가 반환되었는데 의미는 모든 항목에 대해서 
평균적으로 위 숫자만큼 오차가 있다는 것이다. 

참고 : https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=heygun&logNo=221516529668


```python

```
