---
layout: post
title: Ormi_python_06
permalink: /ormi06/
related_posts:
  - ormi/_posts/2023-05-08-python-chapter05.md
  - 
---

## Python_Basic_06

- 목차로 돌아가기[Ormi] [1]

[1]: https://aminsc.github.io/ormi/


* 반복문
    * 정해진 순서를(next) 반복하는 것
    * 형태
    ```python
    # for 변수 in 순회가능한객체: # stopItoration까지 반복
    #     code

    # while 조건: # true까지 반복
    #     code 
    ```
    * 순회 가능한 객체(이터러블 객체) : 문자열, 리스트, 튜플, 딕셔너리, 셋, range, enumerate, map, set, sorted, reverse 등
    * 순회 불가능한 객체 : int, float 등 
    * code 안에서 변수를 사용하지 않을 경우 언더바를 관습적으로 사용합니다.
    ```python
    # for _ in 순회가능한객체:
    #     code
    ```
    * 반복문 다음 else 구문 : break 없이 정상 종료 되면 실행
    * 반복문 안에 break 구문 : 자신을 감싸고 있는 반복문 1개 탈출
    * 반복문 안에 continue 구문 : 다음 루프로 넘어감
    * 반복문 안에 pass : 공백만 채워줄 뿐 아무 기능 없음

* bulit-in function
    * 수학적 통계에 활용되는 함수
        - abs( ) : 괄호 안에 있는 값을 절대값으로 출력해줍니다.
        - all( ) : 괄호 안에 있는 값들이 모두 True(False)일 때 True(False)를 출력합니다.
        - any( ) : 괄호안에 있는 값이 하나라고 True이면 True로 출력합니다.
        - pow( ) : 제곱을 출력합니다.
        - max( ) : 값의 최댓값을 출력합니다.
        - min( ) : 값의 최솟값을 출력합니다.
        - sum( ) : 값의 합계를 출력합니다.
        - len( ) : 문자열의 길이를 출력합니다.
        - sorted( ) : 데이터를 정렬해줍니다.
        - reversed( ) : 정렬되지 않은 상태에서 값을 역순으로 출력합니다.

    * 형변환 함수
        - set( )
        - dict( )
        - hex( ) : 16진법
        - bin( ) : 2진법
        - oct( ) : 8진법
        - bool( )
        - str( )
        - ord( ) : 각각의 문자에 대한 숫자값을 출력해줍니다.(유니코드표를 참고하세요.)
        - float( )
        - tuple( )
        - chr( ) : 숫자값을 통해서 문자를 출력합니다.
        - list( )
        - range( )
        - complex( )

    * 도움말
        - help( )

    * object 관련 함수
        - dir( )
        - id( )
        - type( )

    * 순회 가능한 객체
        - enumerate( ) : 값에 순위를 매기고 싶을 때 사용합니다.
        - range( )
        - sorted( )
        - reversed( )
        - filter( )
        - zip( )
        - map( )

* args, kargs
    * 가변 아규먼트, 가변 키워드 아규먼트
    ```python
    def print_args(*args): # 꼭 args가 될 필요는 없습니다.
        print(args)

    print_args(100, True, 'honggildong')

    ####

    def print_kwargs(**kwargs): # 꼭 kargs가 될 필요는 없습니다.
    print(kwargs)

    print_kwargs(name='honggildong', age='10')
    ```

* lambda
    * lambda 는 익명함수라고 하며, 이름이 없는 함수
    * 보통은 다시 사용되지 않을 함수를 선언할 때 사용
    ```python
    leehojun = lambda x : x**2

    # def leehojun(x):
    #     return x ** 2

    list(map(lambda x : x ** 2, [1, 2, 3, 4]))
    ```