---
layout: post
title: Ormi_python_08
permalink: /ormi08/
related_posts:
  - ormi/_posts/2023-05-10-python-chapter07.md
  - ormi/_posts/2023-05-12-python-chapter09.md
---

## Python_Basic_08

- 목차로 돌아가기[Ormi] [1]

[1]: https://aminsc.github.io/ormi/


* 제너레이터
    * 제너레이터란, 이터레이터(순회 가능한 객체)를 생성해주는 함수
    * 예제 1
        ```python
        def gen():
            count = 0
            while True:
                yield count
                count += 1
        for i in gen():
            print(i)
            if i == 10:
                break
        ```
* 데코레이터
    * 함수 앞 뒤로 다른 역활을 해주는 기능을 붙이고 싶을 때 사용
    * 코드 예
        ```python
        def print_hello(func):
            def wrap_func():
                print('hello start')
                func()
                print('hello end')
            return wrap_func

        @print_hello
        def func1():
            print('func1 입니다.')

        func1()
        ```

* 파이썬 모듈
    * 모듈 : 함수나 변수 또는 클래스를 모아 놓은 파이썬 파일
    * 패키지 : 파이썬 모듈들을 계층적으로 관리
    * 모듈 사용 예1
    ```python
    # 같은 폴더 내 test1.py
    name = 'leehojun'
    age = 10

    def hello():
        pass

    class Human():
        pass

    # 같은 폴더 내 실행 파일
    import test1

    print(test1.name)
    print(test1.hello())
    ```
    * 예2
    ```python
    # 연습 3 (폴더 > 파일 생성)
    # one이라는 것이 여기서는 폴더입니다!
    # two가 file 이름이에요.
    from one import two

    print(two.name)
    ```
    * 예3
    ```python
    # 연습 4 (폴더 > 폴더 > 파일 생성)
    # 런타임 재시작 하세요!
    from one.two import three

    print(three.name)
    ```

* 파일 입출력
    * 파일을 읽고 쓰는 것
        * 파일 쓰기
        ```python
        f = open('programminglanguage.txt', 'w') 
        # 파일모드 : r(read), w(write, 처음부터 덮어씁니다.), a(append)
        s = 'hello\nworld'
        f.write(s)
        f.close()
        ```
        * 파일 읽기
        ```python
        f = open('programminglanguage.txt', 'r')
        while True:
            line = f.readline()
            if not line:
                break
            print(line)
        f.close()
        ```
        ```python
        f = open('programminglanguage.txt', 'r')
        data = f.read()
        print(data)
        f.close()
        ```