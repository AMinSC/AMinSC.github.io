---
layout: post
title: Ormi_python_03
permalink: /ormi03/
related_posts:
  - ormi/_posts/2023-05-02-python-chapter02.md
  - ormi/_posts/2023-05-04-python-chapter04.md
---

## Python_Basic_03

- 목차로 돌아가기[Ormi] [1]

[1]: https://aminsc.github.io/ormi/


1. 함수
    1. 코드 덩어리(정말 쉽게 설명하면)
    2. 코드를 재사용 할 수 있으며, 실수를 줄일 수 있습니다.
    3. 코드의 구조를 한 눈에 파악할 수 있습니다.
    4. 형태
        ```python
        # 파선아실(파라미터는 선언할 때, 아규먼트는 실제)
        def function(x, y):
            z = x + y
            return z
        print(f'function(5, 7) = {function(5, 7)}')
        ```
    5. 함수 안에 함수와 함수 안에 변수는 밖에서 접근이 불가합니다.
    6. 지역 변수와 전역 변수
        * 전역변수 : 전역에서 접근할 수 있는 변수
        * 지역변수 : 함수 내에서만 접근할 수 있는 변수
        ```python
        # 전역변수는 각 함수에서 접근은 가능하지만 수정이 되진 않습니다.
        # only read
        # global이라는 키워드로 밖에 있는 변수를 수정할 수도 있지만 권하지 않습니다.
        # 권하지 않기에 요약자료에도 없습니다.
        a = 100
        def f():
            a = a + 1
        f()
        ```
    7. 재귀함수
        * 내가 나를 호출하는 것입니다.
        * 재귀 <-> for문은 대부분 호환이 가능합니다.
        * 반복문 사용하시기를 권합니다!
        * 어렵고 효율도 안좋아요! (얼마나 효율이 안좋은지도 확인해보겠습니다.)
        * 필수적으로 사용하는 곳이 있습니다.
        ```python
        def f(n):
            if n <= 1:
                return 1
            else:
                return n * f(n-1)

        f(5)
        ```
2. list (리스트)
    * 순서를 가진 데이터들의 집합(Sequence)
    * 리스트는 값의 변경
    * 리스트 안에 리스트로 다차원의 리스트를 만드는 것도 가능
    * 리스트 안에 다른 딕셔너리, 셋, 튜플 등을 넣는 것도 가능합니다
    ```python
    l = [10, 20, 30, 40]
    print(l[0]) # 순서로 값 호출
    l[0] = 1000 # 값의 변경 가능
    print(l)

    data = [[1, 2, 3], # 다차원 배열
        [4, 5, 6],
        [7, 8, 9]]

    print(data)
    ```
    * 리스트 메서드
        * append : 맨 뒤에 값 추가
        * clear : 모든 값 지우기
        * copy : 얕은 복사
        * count : 갯수 세기
        * extend : 확장하기(뒤에 순회 가능한 객체가 들어오면 순차적으로 추가)
        * index : 위치 찾기
        * insert : 삽입하기
        * pop: 맨 뒤에서 값 꺼내기(index가 들어오면 index에서 값 꺼냄)
        * remove : 값 지우기
        * reverse : 역순
        * sort : 정렬