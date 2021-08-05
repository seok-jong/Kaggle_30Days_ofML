# Day3

## **Functions and Getting Help**

### 1. Getting Help

help() 메소드는 인수로 들어간 클래스나 함수에 대해서 도움말을 출력하는 메소드이다. 

ex)

```python
help(round)
>>>
round(number, ndigits=None)
    Round a number to a given precision in decimal digits.
    
    The return value is an integer if ndigits is omitted or None.  Otherwise
    the return value has the same type as the number.  ndigits may be negative.

```





### 2. Defining functions

파이썬에 내장된 함수 말고 직접 함수를 작성하여 이용할 수 있다. 
함수는 입력을 받고 해당 기능을 수행한 뒤 결과를 반환한다. 어떠한 기능에 대하여 반복적으로 수행해야 한다면 코드를 불필요하게 반복입력하는 행위를 줄이기 위해 함수를 이용할 수 있다. 

```python
def least_difference(a, b, c):
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    return min(diff1, diff2, diff3)
```



### 3. Docstrings

Docstrings은 함수나 class 에 대한 설명을 말하며 위에서 알아본 help() 로 해당 함수를 호출하면 출력되는 설명이 바로 Docstrings이다. 

```python
def least_difference(a, b, c):
    """Return the smallest difference between any two numbers
    among a, b and c.
    
    >>> least_difference(1, 5, -5)
    4
    """
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    return min(diff1, diff2, diff3)
```

위 코드처럼 함수를 정의하고 바로 아래에 ```을 이용하여 함수에 대한 설명을 입력하는 방식으로 이용할 수 있다. 

