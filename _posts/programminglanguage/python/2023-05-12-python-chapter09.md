---
layout: post
permalink: /python/basic09/
categories: [python]
related_posts:
  - _posts/programminglanguage/python/2023-05-09-python-chapter08.md
  - 
---

# 에러처리, 파일입출력
## Python_Basic_09

- [Python 목차로 돌아가기] [1]

[1]: https://aminsc.github.io/python/


* 애러처리
    * Python에서는 애러를 만나면 코드가(서비스가) 멈춥니다.
    * 예제
        ```python
        try:
            # 예외가 발생할 가능성이 있는 코드
        except:
            # 예외 처리 코드
        else:
            # 예외가 발생하지 않을 때 실행되는 코드
        finally:
            # 예외 발생 여부와 상관없이 항상 실행되는 코드
        ```
* 파일입출력
    * 열기와 닫기를 동시에
    ```python
    with open('test.txt', 'w') as f:
	    f.write('Life is too short, you need programminglanguage')
    ```
    
    * 파일에 추가
    ```python
    f = open('programminglanguage.txt', 'a') # 다시 write 모드로 하면 처음부터 덮어 씁니다.
    s = ''
    for i in range(5, 11):
        s += f'{i}명 참여 중입니다. \n'
    f.write(s)
    f.close()
    ```