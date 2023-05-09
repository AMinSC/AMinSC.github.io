---
layout: post
title: Ormi_python_01
permalink: /ormi01/
related_posts:
  - ormi/_posts/2023-05-01-learn-python-in-ormi.md
  - ormi/_posts/2023-05-02-python-chapter02.md
---

## Python_Basic_01


- 목차로 돌아가기[Ormi] [1]

[1]: https://aminsc.github.io/ormi/


1. 단축키
    * (필수) Ctrl(Command) + Enter : 해당 셀 실행
    * (필수) Alt(Option) + Enter : 해당 셀 실행 + 코드 불록 하단 추가
    * (필수) Ctrl + / : 주석
    * (필수) Shift + Del : 한 줄 지우기
    * (필수) Tab, Ctrl + ] : 들여쓰기
    * (필수) Shift + Tab, Ctrl + [ : 내어쓰기

2. 마크다운
    ```
    # hello
    ## hello
    ### hello

    1. hello
    2. hello
    3. hello

    * hello
    * hello
    * hello
    ```

3. 주석

    ```python
    #행 단위 주석입니다.

    """
    큰 따옴표로 세번 묶거나
    작은따옴표로 세번 묶으면
    열단위 주석이 됩니다.
    """

    '''
    큰 따옴표로 세번 묶거나
    작은따옴표로 세번 묶으면
    열단위 주석이 됩니다.
    '''
    ```

4. PEP8 권고사항
    * 띄어쓰기는 4칸
    * 한 줄에 79자 이상을 사용하지 않는다.

5. 형의 종류(type, dir)
    * 컨벤션 자료형(list, tuple, dict, set)은 나중에 진행합니다.
    * int
    * float
    * bool
    * str
    * function
    * bulit-in function

6. 이스케이프 문자
    * https://ko.wikipedia.org/wiki/%EC%9D%B4%EC%8A%A4%EC%BC%80%EC%9D%B4%ED%94%84_%EB%AC%B8%EC%9E%90
    ```python
    print('hello \n world')
    print('hello \t world')
    print('hello \' world')
    print('hello \" world')
    print('hello \\ world')
    ```

7. 실무에서 자주 사용하는 타입확인 구문
    ```python
    type(10)
    type(10) == int
    type(10.1) == float

    a = 10
    isinstance(a, int)
    isinstance(a, float)
    ```

8. 변수의 인사이트
    ```
    dir을 입력했을 때
    1. __hello__와 같은 형태의 메직 메서드는 속성을 표현한다
    2.  언더바가 없는 메서드는 해당 자료형의 편의 기능을 제공한다
    ```

9. 입력과 출력
    ```python
    x = input() #입력, 숫자를 입력해도 str
    print(x) #출력

    이름 = '홍길동'
    나이 = 10
    print(f'제 이름은 {이름}입니다. 제 나이는 {나이}입니다.')
    print(f'{100 * 10}')
    ```


10. int 형
    * 2진수, 8진수, 16진수는 정수


11. float 형
    * 부동소수점 오차(2진법으로 변환했을 때 0.1이 무한대수가 발생합니다.)
    0.1 + 0.2 # 대부분의 언어 공통입니다.
    * https://docs.python.org/ko/3/tutorial/floatingpoint.html
    * https://0.30000000000000004.com/ 에서 언어별 해결책을 제시한다.