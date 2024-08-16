---
layout: post
permalink: /python/basic05/
categories: [python]
description: >
  조건문, 반복문
related_posts:
  - _posts/programminglanguage/python/2023-05-04-python-chapter04.md
  - _posts/programminglanguage/python/2023-05-09-python-chapter06.md
---

# Python_Basic_05
## 조건문, 반복문

- [Python 목차로 돌아가기] [1]

[1]: https://aminsc.github.io/python/


* 조건문
    * 조건에 따라 코드를 분기할 수 있는 구문
    * if, elif, else
    * elif와 else는 단독으로 사용이 되지 않습니다.
    * 예시(score에 값을 변경해보면서 money 값을 확인해주세요.)
    ```python
    score = 81
    money = 0

    if score >= 90: # 만약에 조건이 참이라면
        print('mom : i\'m so happy!')
        money += 1000000
    elif score >= 80: # 그렇지 않고 만약에 조건이 참이라면
        print('mom : i\'m happy!')
        money += 100000
    elif score >= 70: # '그렇지 않고 만약에'에서 '그렇지 않고'가 만족이 안되기 때문에 실행하지 못합니다.
        print('mom : i\'m so...!')
        money += 10000
    elif score >= 60:
        print('mom : i\'m so...!')
        money += 1000
    else:
        print('mom : i\'m...!')
    print(money)
    ```
    * 3항 연산자
    ```python
    def f(y):
    return 'one' if y > 80 else None
    ```
* 정해진 순서를(next) 반복하는 것
    * 형태
    ```python
    # for 변수 in 순회가능한객체:
    #     code
    ```
    * 순회 가능한 객체(이터러블 객체) : 문자열, 리스트, 튜플, 딕셔너리, 셋, range, enumerate, map, set, sorted, reverse 등
    * 순회 불가능한 객체 : int, float 등 
    * code 안에서 변수를 사용하지 않을 경우 언더바를 관습적으로 사용합니다.
    ```python
    # for _ in 순회가능한객체:
    #     code
    ```