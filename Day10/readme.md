# Day10




## 1. Underfitting and Overfitting

최근에 나온 성능좋은 문제도 언더피팅과 오버피팅은 중요하게 신경쓰고 해결해야 하는 문제이다. 

1) ```overfitting``` 이란 모델이 학습데이터에 대해서 너무 과하게 학습되어 새로운 데이터에 대해서 정확도가 떨어지는 현상을 말하며 앞에서 봤던 의사결정트리에서는 모델이 너무 깊어졌을 때 발생한다.   


2) ```underfitting```이란 overfitting과는 반대로 모델이 학습데이터에 대해서 기본적인 특성을 구분 못할 정도로 학습이 덜 된 상황을 말하며 학습데이터의 차원이 높은데 비해 모델의 깊이가 너무 낮거나 학습이 충분히 되지 않으면 발생한다. 의사결정트리에서는 모델의 깊이가 너무 낮을 때 발생한다. 

![image.png](http://i.imgur.com/AXSEOfI.png)

이러한 ```모델의 복잡도```를 상황에 맞게 설정해 주어야 한다. 이러한 작업을 하이퍼파라미터 튜닝이라고 한다. 

의사결정나무에서는 전체 트리의 잎 갯수를 설정하는 것을 예로 들 수 있다.


```python
from sklearn.metrics import mean_absolute_error
from sklearn.tree import DecisionTreeRegressor

def get_mae(max_leaf_nodes, train_X, val_X, train_y, val_y):
    model = DecisionTreeRegressor(max_leaf_nodes=max_leaf_nodes, random_state=0)
    model.fit(train_X, train_y)
    preds_val = model.predict(val_X)
    mae = mean_absolute_error(val_y, preds_val)
    return(mae)
```

위 코드에서 작성한 함수를 이용하여 잎 갯수에 따른 모델의 성능을 살펴봄으로써 우리의 데이터에 어떤 하이퍼 파라미터가 적합한지 찾을 수 있다.

## 2. Random Forests

RandomForests를 간단하게 말하자면 의사결정트리를 여러개 이용하고 각각의 결과값들을 투표형식으로 추합하여 결과를 예측하는 것이다. 


```python
import pandas as pd
from sklearn.model_selection import train_test_split

data_path = "../data/melb_data.csv"
home_data = pd.read_csv(data_path)
# home_data.head()
y=home_data.Price
x=home_data
# x.head()
x=x.select_dtypes(include=['int64','float64'])
x=x.drop(columns=['BuildingArea','YearBuilt','Car'],axis=1)
# x.head()


train_x,val_x,train_y,val_y = train_test_split(x,y,random_state=1)
```


```python
from sklearn.ensemble import RandomForestRegressor

# Define the model. Set random_state to 1
rf_model = RandomForestRegressor(random_state=1)

# fit your model
rf_model.fit(train_x,train_y)

# Calculate the mean absolute error of your Random Forest model on the validation data
predictions=rf_model.predict(val_x)
rf_val_mae = mean_absolute_error(predictions,val_y)

print("Validation MAE for Random Forest Model: {}".format(rf_val_mae))


```

    Validation MAE for Random Forest Model: 363.57486597938157


단순히 모델을 randomForests로 바꾸었을 뿐인데 이전에 의사결정트리로 학습을 진행했을 때보다 성능이 훨씬 좋아진 것을 확인할 수 있다. 
