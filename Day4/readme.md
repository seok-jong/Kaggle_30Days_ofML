# Day4

## **Booleans and Conditionals**



### 1.  Explanation

True , False로 값을 나타내는 클래스로 명제에 대해 표현할 때 이용 

![Screenshot from 2021-08-07 17-50-10](https://user-images.githubusercontent.com/77032455/128594744-84947e2f-30a3-4106-9930-4ee97380ca60.png)

booleans를 사용한 비교연산자는 위 표와 같이 이용한다. 

또한 논리연산자를 사용할 때의 규칙은 아래 표와같다. 

![Screenshot from 2021-08-07 17-52-50](https://user-images.githubusercontent.com/77032455/128594804-c2799753-5473-4e6a-b5f1-e4f458c413c7.png)



한 줄에 여러개의 논리연산자가 복합적으로 사용되는 코드에서는 논리연산자가 오른쪽에서부터 왼쪽으로 순차적으로 수행된다. ( 괄호가 있을 경우에는 괄호 안쪽부터 )



### 2. Exercise

q7. In this problem we'll be working with a simplified version of [blackjack](https://en.wikipedia.org/wiki/Blackjack) (aka twenty-one). In this version there is one player (who you'll control) and a dealer. Play proceeds as follows:

- The player is dealt two face-up cards. The dealer is dealt one face-up card.
- The player may ask to be dealt another card ('hit') as many times as they wish. If the sum of their cards exceeds 21, they lose the round immediately.
- The dealer then deals additional cards to himself until either:
  - the sum of the dealer's cards exceeds 21, in which case the player wins the round
  - the sum of the dealer's cards is greater than or equal to 17. If the player's total is greater than the dealer's, the player wins. Otherwise, the dealer wins (even in case of a tie).

When calculating the sum of cards, Jack, Queen, and King count for 10. Aces can count as 1 or 11 (when referring to a player's "total" above, we mean the largest total that can be made without exceeding 21. So e.g. A+8 = 19, A+8+8 = 17)

```
1. player 는 두 장의 카드를 받는다. dealer는 한 장의 카드를 받는다. 
2. player는 원하는 만큼 dealer에게 카드를 요청할 수 있다.(hit 라고 함) 
   카드의 합이 21을 초과하는 즉시, 해당 round에서 패배한다. 
3. 딜러는 다음 중 하나의 조건을 충족시킬 때까지 카드를 추가로 받는다. 
	1) 딜러의 카드가 21을 초과할 때까지( 이 경우에 player 승리)
	2) 딜러의 숫자 합이 17보다 크거나 동일할 때까지( 이 경우 player의 숫자합이 dealer의 숫자합보다 크면 player의 승이다. 반대로는 dealer의 승리)
```



```python
def should_hit(dealer_total, player_total, player_low_aces, player_high_aces):
    """Return True if the player should hit (request another card) given the current game
    state, or False if the player should stay.
    When calculating a hand's total value, we count aces as "high" (with value 11) if doing so
    doesn't bring the total above 21, otherwise we count them as low (with value 1). 
    For example, if the player's hand is {A, A, A, 7}, we will count it as 11 + 1 + 1 + 7,
    and therefore set player_total=20, player_low_aces=2, player_high_aces=1.
    """

    if dealer_total >= player_total:
        return True
    
    if player_total>=19:
        return False
    if player_total<=11:
        return True
    else:
        if player_high_aces>=1:
            return True

    return False


q7.simulate(n_games=50000)

>>>
Player won 21048 out of 50000 games (win rate = 42.1%)
```

