---
layout: post
permalink: /pl/python05/
categories: [python]
related_posts:
  - _posts/programminglanguage/python/2023-05-01-python-chapter01.md
  - _posts/programminglanguage/python/2023-05-01-python-chapter03.md
---

## Python_Basic_02

- 목차로 돌아가기[Python] [1]

[1]: https://aminsc.github.io/pl/python/

1. str
    - 순서가 있는 **시퀀스 자료형**입니다.
    - 작은 따옴표(' ')나 큰 따옴표(" "), 삼중따옴표('''str''', """str""")로 감싸는 것도 가능합니다. (삼중따옴표를 사용할 경우에는 줄단위의 문자열을 나타낼 수 있습니다.)
    - 작은 따옴표 안에 큰 따옴표, 큰 따옴표 안에 작은 따옴표 사용이 가능합니다.
    - 이스케이프 문자도 사용이 가능합니다.
    - 리스트, 튜플도 시퀀스 자료형입니다.
    - 메서드
        - lower
        - index, find
        - count
        - strip
        - replace
        - split, join
        - isdigit
2. 슬라이싱
    - 시퀀스형 자료형을 자를 수 있습니다.
    - 형태
    ```
    # s[start:stop:step]
    s = 'paullab CEO leehojun'
    s[5:]
    s[:5]
    s[3:10]
    s[:]
    s[0:20:2]
    # 자주 사용되는 코드
    s = 'paullab CEO leehojun!'
    s[:] # string에서는 많이 사용하지 않지만 list에서 많이 사용합니다.
    s[:-1] # 마지막 요소만 제외하고 다 슬라이싱 합니다.
    ```

3. 형변환
    - 형변환 : type을 변경하는 것입니다.
    - int, float, str 등 자료형에 이름으로 형태를 변경할 수 있습니다.
    - 그 중에서도 bool이 매우 중요합니다.
    ```
    # 별 5개
    # bool 형으로 형변환 하는 것
    if True:
        print('hi')

    if 'hello':
        print('hi')

    # 정말 많이 사용하는 코드
    l = [1, 2, 3]
    while l:
        print(l.pop())

    bool('') # 빈 문자열을 제외하고 모두 True
    bool('a')
    bool('False') # 문자열 False이기 때문에 True
    bool(0) # 0을 제외하고 모두 True
    bool(-1)
    bool(100)
    bool(None) # None은 비어있음을 명시해주는 키워드, False
    bool([]) # 컨벤션 자료형은 비어있으면 False입니다.
    bool({})
    ```

4. 산술연산
    ```
    a = 10
    b = 3

    print(f'10 + 3 == {a + b}')
    print(f'10 - 3 == {a - b}')
    print(f'10 / 3 == {a / b}')
    print(f'10 // 3 == {a // b}') # 몫만 나옵니다.(정수만요!)
    print(f'10 * 3 == {a * b}')
    print(f'10 ** 3 == {a ** b}')
    print(f'10 % 3 == {a % b}') # 나머지
    ```

5. 논리연산
    ```
    # and 는 곱
    # or 는 합
    # not은 반대
    # True 1
    # False 0
    # 중요한 포인트는 저렇게 했을 때 언제 True가 되는지 정리하는 것

    print(True and False)
    print(True or False)
    print(True or True)

    # https://codingdojang.com/scode/350?answer_mode=hide
    for i in range(101):
        if i % 3 == 0 and i % 5 == 0:
            print(i)
    ```

6. 할당연산
    ```
    a = 10
    a += 10 # a = a + 10
    a //= 2
    a
    ```

7. is, in
    1. is
        ```
        a = [1, 2, 3]
        b = [1, 2, 3]

        id(a), id(b)
        a == b # 값이 같은 것과 메모리에 같은 공간에 저장되어 있다는 얘기는 다른 얘기입니다!
        ```
    2. in
        ```
        'a' in 'helalo world'
        'a' in 'hello world'
        'a' in ['a', 'b']
        'a' in {'a':10, 'b':20}
        # 10 in {'a':10, 'b':20} # dict안에있는 value값이 있는지 확인하고 싶으면
        10 in {'a':10, 'b':20}.values()
        10 in {10, 20, 30}
        ```