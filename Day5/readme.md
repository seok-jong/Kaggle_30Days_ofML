# Day5

## List & Loops and List Comprehensions



### 1. List

1) 대괄호 [ ] 로 묶여있는 자료형들의 시퀀스
2) [3] 과 같이  index로 요소에 접근가능
3) [0:3] 과 같이 slicing 가능 
4) 요소로 int,str,dict,list,set,tuple등의 여러가지 자료형이 올 수 있음
5) len() 메소드를 사용하여 리스트의 길이 반환
6) sorted() 메소드를 이용해 리스트의 요소를 정렬 가능 
7) sum() 메소드를 사용하여 요소의 총합을 반환 
8) max() 메소드를 사용해 요소의 최댓값 반환 
9) list.append() 메소드를 이용해 list에 요소 추가 
10) list.pop() 메소드를 통해 리스트의 가장 뒤쪽 (index= -1) 요소 반환 및 삭제
11) list.index() 메소드를 이용해 요소의 index 반환 
12) in 연산자를 이용해 리스트 안의 요소 존재 유무 판단 



### 2. Loops and List Comprehensions

#### 1) Loops

- for 또는 while을 통하여 작성 
- for + list(시퀀스 자료형)을 조합하여 자주 사용 

#### 2) List Comprehensions

- ```python
  # ex)
  [n**2 for n in range(10)]
  ```

- for 문과 if 문이 같이 쓰일 수 있음 

- ```python
  short_planets = [planet for planet in planets if len(planet) < 6]
  short_planets
  
  >>>
  ['Venus', 'Earth', 'Mars']
  ```

