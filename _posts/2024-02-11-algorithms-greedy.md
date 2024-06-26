---
layout: post
title: 그리디 알고리즘
tags: [알고리즘, 그리디 알고리즘]
categories: [알고리즘, 그리디 알고리즘]
image:
  path: /assets/img/post/algorithm/greedy.jpeg
  alt: greedy
date: 2024-02-11 16:13 +0900
---

## 그리디 알고리즘

그리디 알고리즘(Greedy Algorithm)은 **최적화 문제를 해결하는 데 사용되는 알고리즘 중 하나**로, **매 순간 최적이라고 생각되는 선택을 하여 최종적인 해답에 도달하는 방법**이다. 그러나 모든 최적화 문제에서 그리디 알고리즘이 최적해를 보장하는 것은 아니다. 그리디 알고리즘이 효과적으로 작동하려면 **문제가 그리디 선택 속성(Greedy Choice Property)과 최적 부분 구조(Optimal Substructure)를 만족**해야 한다.

### 그리디 선택 속성 (Greedy Choice Property)

그리디 선택 속성은 지역적으로 최적의 선택을 해도 전체적으로 최적의 해결책을 구할 수 있다는 속성이다. 즉, **각 단계에서 선택이 이후의 선택에 영향을 미치지 않으며**, 이러한 지역적인 최적의 선택들이 결합하여 전체 문제의 최적해를 이끌어 낼 수 있다.

### 최적 부분 구조 (Optimal Substructure)

최적 부분 구조는 문제의 최적 해결책이 그 문제의 부분 문제들의 최적 해결책으로부터 구성될 수 있다는 속성이다. 즉, **전체 문제의 최적해를 구하기 위해서는 부분 문제들 또한 최적으로 해결**되어야 한다.

### 접근 방법

- **문제 분석**: 문제를 이해하고, 문제가 그리디 알고리즘을 사용하여 해결할 수 있는지 분석한다.
- **알고리즘 설계:** 그리디 기준에 따라 **매 순간 최적의 선택을 하도록 알고리즘을 설계**한다.
- **최적해 검증**: 설계한 알고리즘이 **실제로 문제의 최적해를 제공하는지 검증**한다.

### 장단점

- **장점**
  - **간단하고 직관적**: 그리디 알고리즘은 **문제를 해결하는 과정이 간단하며, 구현이 쉽다**.
  - **효율적인 실행 시간**: 많은 경우에서 그리디 알고리즘은 **다른 알고리즘에 비해 빠른 실행 시간**을 보인다. 이는 매 순간 최적의 선택만을 고려하기 때문에 발생하는 현상이다.
- **단점**
  - **최적 해 보장 어려움**: 그리디 알고리즘은 **항상 최적 해를 찾는 것을 보장하지 않는다**.

### 동전 교환 문제

동전 교환 문제에서는 **주어진 금액을 만들기 위해 필요한 최소한의 동전 개수를 찾는 문제**이다. 예를 들어, 사용할 수 있는 동전의 종류가 1원, 5원, 10원, 25원이고, 만들어야 하는 금액이 32원이라면, 그리디 알고리즘을 사용하여 25원 1개, 5원 1개, 1원 2개를 선택하면 총 4개의 동전으로 금액을 만들 수 있다.

**예시 코드**

```python
def min_coins(coins, amount):
    """
    coins: 사용할 수 있는 동전의 목록
    amount: 만들어야 하는 금액
    return: 최소 동전 개수
    """
    # 동전의 종류를 내림차순으로 정렬
    coins.sort(reverse=True)

    # 동전 개수를 저장할 변수
    count = 0

    # 동전의 종류를 하나씩 확인하면서
    for coin in coins:
        # 현재 동전으로 만들 수 있는 최대한을 만들고 남은 금액을 계산
        count += amount // coin # // = 정수 몫
        amount %= coin # // % 나머지

        # 모든 금액을 만들었다면 반복 종료
        if amount == 0:
            break

    return count

# 사용자 입력 처리
input_coins = input("사용할 수 있는 동전의 종류를 쉼표로 구분하여 입력하세요 (예: 1,5,10,25): ")
input_amount = int(input("만들어야 하는 금액을 입력하세요: "))

# 문자열을 정수 리스트로 변환
coins = list(map(int, input_coins.split(',')))

# 최소 동전 개수 계산
min_coin_count = min_coins(coins, input_amount)

# 결과 출력
print(f"최소 동전 개수: {min_coin_count}")
```
