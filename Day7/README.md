# Day7

파이썬은 ```import``` 메소드를 이용해서 손쉽게 모듈이나 패키지를 가져와 사용할 수 있다. 

## 1. import 

```python
import math
import numpy as np
```

위 코드처럼 import를 사용하여 라이브러리를 불러오며 

```python
from math import pi
```

위 코드처럼 from a import 문을 써서 라이브러리에서 특정 요소만 가져와 사용할 수 있다. 

import 뒤에 ```*```을 입력하여 모든 요소를 다 가져와 사용할 수 있는데 이런 경우엔 두 라이브러리에서 같은 이름의 요소가 있다면 type 에러가 발생할 수 있다. 



## 2. Exercise

1) This is a very challenging problem. Don't forget that you can receive a hint!

   Luigi is trying to perform an analysis to determine the best items for winning races on the Mario Kart circuit. He has some data in the form of lists of dictionaries that look like...

   ```
   [
       {'name': 'Peach', 'items': ['green shell', 'banana', 'green shell',], 'finish': 3},
       {'name': 'Bowser', 'items': ['green shell',], 'finish': 1},
       # Sometimes the racer's name wasn't recorded
       {'name': None, 'items': ['mushroom',], 'finish': 2},
       {'name': 'Toad', 'items': ['green shell', 'mushroom'], 'finish': 1},
   ]
   ```

   `'items'` is a list of all the power-up items the racer picked up in that race, and `'finish'` was their placement in the race (1 for first place, 3 for third, etc.).

   He wrote the function below to take a list like this and return a dictionary mapping each item to how many times it was picked up by first-place finishers.

   

   ```python
   # Import luigi's full dataset of race data
   from learntools.python.luigi_analysis import full_dataset
   
   # Fix me!
   def best_items(racers):
       winner_item_counts = {}
       for i in range(len(racers)):
           # The i'th racer dictionary
           racer = racers[i]
           # We're only interested in racers who finished in first
           if racer['finish'] == 1:
               for i in racer['items']:
                   # Add one to the count for this item (adding it to the dict if necessary)
                   if i not in winner_item_counts:
                       winner_item_counts[i] = 0
                   winner_item_counts[i] += 1
   
           # Data quality issues :/ Print a warning about racers with no name set. We'll take care of it later.
           if racer['name'] is None:
               print("WARNING: Encountered racer with unknown name on iteration {}/{} (racer = {})".format(i+1, len(racers), racer['name']))
       return winner_item_counts
   
   # Try analyzing the imported full dataset
   print(best_items(full_dataset))
   print(full_dataset)
   ```

   위 코드에서의 문제점은 for문이 중첩되어 사용되는 경우에 i라는 변수를 중복하여 사용했다는 점이다. 이는 위에서 from import *에서 중복된 요소를 가져왔을 때 발생하는 type error와 유사하며 변수나 클래스,함수의 이름을 설정할 때에 주의해야 한다.

   ```python
   # Import luigi's full dataset of race data
   from learntools.python.luigi_analysis import full_dataset
   
   # Fix me!
   def best_items(racers):
       winner_item_counts = {}
       for i in range(len(racers)):
           # The i'th racer dictionary
           racer = racers[i]
           # We're only interested in racers who finished in first
           if racer['finish'] == 1:
               for item in racer['items']:
                   # Add one to the count for this item (adding it to the dict if necessary)
                   if item not in winner_item_counts:
                       winner_item_counts[item] = 0
                   winner_item_counts[item] += 1
   
           # Data quality issues :/ Print a warning about racers with no name set. We'll take care of it later.
           if racer['name'] is None:
               print("WARNING: Encountered racer with unknown name on iteration {}/{} (racer = {})".format(i+1, len(racers), racer['name']))
       return winner_item_counts
   
   # Try analyzing the imported full dataset
   print(best_items(full_dataset))
   print(full_dataset)
   ```

   내부 for문의 i라는 변수를 item이라는 변수로 바꿔주면 정상적으로 작동한다. 

   
   

2) Suppose we wanted to create a new type to represent hands in blackjack. One thing we might want to do with this type is overload the comparison operators like `>` and `<=` so that we could use them to check whether one hand beats another. e.g. it'd be cool if we could do this:

   ```
   >>> hand1 = BlackjackHand(['K', 'A'])
   >>> hand2 = BlackjackHand(['7', '10', 'A'])
   >>> hand1 > hand2
   True
   ```

   Well, we're not going to do all that in this question (defining custom classes is a bit beyond the scope of these lessons), but the code we're asking you to write in the function below is very similar to what we'd have to write if we were defining our own `BlackjackHand` class. (We'd put it in the `__gt__` magic method to define our custom behaviour for `>`.)

   Fill in the body of the `blackjack_hand_greater_than` function according to the docstring.

   ```python
   def get_score(hand):
   #     print(hand)
       a_count=0
       score=0
       for i in hand:
           if i in["Q","K","J"]:
               score+=10
           elif i=="A":
               a_count+=1
               continue
           else:
               score+=int(i)
   
       
       for i in range(a_count):
           score+=11
           if score>21:
               score-=10
   #     print("a_count = ",a_count)
   #     print("score = ", score)
       return score
   
       
       
   def blackjack_hand_greater_than(hand_1, hand_2):
       """
       Return True if hand_1 beats hand_2, and False otherwise.
       
       In order for hand_1 to beat hand_2 the following must be true:
       - The total of hand_1 must not exceed 21
       - The total of hand_1 must exceed the total of hand_2 OR hand_2's total must exceed 21
       
       Hands are represented as a list of cards. Each card is represented by a string.
       
       When adding up a hand's total, cards with numbers count for that many points. Face
       cards ('J', 'Q', and 'K') are worth 10 points. 'A' can count for 1 or 11.
       
       When determining a hand's total, you should try to count aces in the way that 
       maximizes the hand's total without going over 21. e.g. the total of ['A', 'A', '9'] is 21,
       the total of ['A', 'A', '9', '3'] is 14.
       
       Examples:
       >>> blackjack_hand_greater_than(['K'], ['3', '4'])
       True
       >>> blackjack_hand_greater_than(['K'], ['10'])
       False
       >>> blackjack_hand_greater_than(['K', 'K', '2'], ['3'])
       False
       """
       s_1=get_score(hand_1)
   #     print("------------")
       s_2=get_score(hand_2)
   #     print("------------")
       
       if s_1 >21:
           return False
       elif s_2>21:
           return True
       elif s_1>s_2:
           return True
       else:
           return False
      
   
   # Check your answer
   q3.check()
   ```

   이 문제의 힌트는 helper함수를 만드는 것이었다. 
   그래서 get_score라는 점수를 계산하는 함수를 위에 정의해 주었고 blackjack_hand_greater_than()함수는 get_score를 통해 나온 값을 비교하여 결과를 출력해준다. 

   helper함수인 get_score함수를 작성하는데 주의해야 할 점은 다음과 같다.

   - Q,K,J 로 이루어진 요소는 10으로 바꿔준다.
   - A 요소를 가지고 있을 경우 따로 a_count라는 변수에 그 갯수를 저장한다.
   - A를 제외한 모든 값을 더하고 그 값에 1차적으로 A를 11로 가정하여 더하고 그 값이 21을 초과할 경우 1로 바꾸어( 10을 빼주어) 적용시킨다.
   - 위 과정을 모두 적용시키면 21을 초과할 경우 최소값으로 , 21을 초과하지 않을 경우 최댓값으로 값을 반환한다. 

   

