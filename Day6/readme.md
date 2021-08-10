# Day6

## Strings and Dictionaries

이 번 챕터는 strings 과 dictionaries에 대해서 배운다. 

### 1. Strings

#### 1) syntax

strings는 문자열을 표현하는 방법이며 ``` "" ```,``` ' ' ```으로 묶어준다.

```python
print("Pluto's a planet!")
print('My dog is named "Pluto"')

>>>
Pluto's a planet!
My dog is named "Pluto"
```



문자열 내부에 특수문자를 포함하려면 ```\```(이스케이프 문자)를 입력하고자 하는 특수문자 앞에 입력한다.

![Screenshot from 2021-08-10 16-51-42](https://user-images.githubusercontent.com/77032455/128829431-8b2f7392-65ec-4a1c-9173-4e70d611e347.png)

```python
'Pluto\'s a planet!'

>>>
"Pluto's a planet!"
```



또한 ``` """ 	```로 묶어서 문자열을 표현할 수 있는데, 이 경우엔 문자열 중간에 입력된 특수문자들이 그대로 출력된다. 

```python
triplequoted_hello = """hello
world"""
print(triplequoted_hello)

>>>
hello
world
```



#### 2) sequences

string도 list와 같이 시퀀스데이터이기 때문에 인덱스를 통해서 원소에 접근이 가능하다.

```python
planet = 'Pluto'
planet[0]

>>>
'P'
------------------------------------------------------------------------
# Slicing
planet[-3:]

>>>
5
```



#### 3) methods

```python
string.upper() # 대문자로 변환 
string.lower() # 소문자로 변환 
string.index("plan") # 해당 문자가(plan) string에 위치한 index 반환(첫 글자 index)
string.startswith("pluto") # 해당 문자(pluto)로 시작하는지 bool로 반환 
string.endswith("planet") # 해당 문자(pluto)로 끝나는지 bool로 반환 
```



```.split()``` 과 ```.join()``` 은 string을 다룰때 굉장히 유용하게 쓰인다. 

```.split()``` : 특정 문자를 기준으로 string을 나누어서 list형태로 반환한다. 

```.join()``` : list를 특정 문자를 사이에 껴서 하나의 string으로 반환한다.

```python
words = claim.split()
words

>>>
['Pluto', 'is', 'a', 'planet!']
--------------------------------------------------------------------------

'/'.join([month, day, year])

>>>
'01/31/1956'
```



[**그 외 문자열 지정자와 포매팅 관련 자료 링크**](https://dojang.io/mod/page/view.php?id=2299) 

### 2. Dictionaries

dict는 key , value 로 구성된 자료형이다. 

```python
numbers = {'one':1, 'two':2, 'three':3} 
          # key  value
```

위 코드처럼 구성되며 

아래 코드처럼 접근 가능하다.

```python
numbers['eleven'] = 11
numbers

>>>
{'one': 1, 'two': 2, 'three': 3, 'eleven': 11}
```







