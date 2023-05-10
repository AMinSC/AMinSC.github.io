---
layout: post
title: Ormi_python_07
permalink: /ormi07/
related_posts:
  - ormi/_posts/2023-05-09-python-chapter06.md
  - 
---

## Python_Basic_07

- 목차로 돌아가기[Ormi] [1]

[1]: https://aminsc.github.io/ormi/


* 클래스
    * 클래스는 데이터(멤버)와 기능(메서드)을 가지고 있는 인스턴트 객체를 생성하기 위한 역할
    * 우리가 배우고 있는 Python을 객체 지향 프로그래밍 언어
        ```
        현실                                코드
        차 ---------------------------> class Car()
        정수 -------------------------> class int()
        실수 -------------------------> class float()

        인간이 만들어 
        놓은 현실 세계에서의 
        정의 또는 약속 --------------> class
        
        1 + 1 = 2가 컴퓨터 입장에서는 10일 수도 있고
        'A' + 'A' = 'AA'가 아니라 컴퓨터 입장에서는 130일 수 있습니다.
        현실세계에서 '인간끼리' 약속을 코드에 세계로 옮긴거에요.
        ```
    * 예제 1
        ```python
        # 메서드 : 클래스 내에 함수
        # 멤버 : 클래스 내에 변수
        # 애트리뷰트 : 멤버 + 메서드
        class CarFactory(object):
            max_speed = 300
            max_people = 5
            def move(self):
                print('차가 움직이고 있습니다.')
            def stop(self):
                print('차가 멈췄습니다.')

        k5 = CarFactory()
        k3 = CarFactory()
        k5.move()
        k3.move()
        k5.stop()
        k3.stop()
        print(k5.max_speed)
        ```
    * 예제2
        ```python
        # 클래스 변수
        # 클래스 바로 하위에 자리하고 있으며
        # 모든 인스턴스가 공유합니다.
        # 인스턴스 변수
        # 인스턴스 영역 안에서만 사용하는 변수
        class Car(object):
            # kinds가 인스턴스에 없기에 class변수로 접근
            # speed는 값을 = 로 할당했기에 인스턴스변수 생성
            kinds = []
            speed = 300
            def add_kinds(self, name):
                self.kinds.append(name) # self.kinds = [name]로 사용하면 인스턴스 변수가 됩니다.
            def change_speed(self, speed):
                self.speed = speed

        k5 = Car()
        k3 = Car()
        k5.speed = 500
        k3.speed # 클래스 변수는 값을 공유한다고 했는데?
        ```
    * 예제3
        ```python
        # 쉽고 중요한 예제!
        # 이 코드는 가능하면 손으로 2 ~ 3번 써보시길 권해드립니다.

        class BlogFactory(object):
            def __init__(self, 제목, 내용, 조회수, 글쓴이, 생성날짜):
                self.title = 제목
                self.content = 내용
                self.count = 조회수
                self.writer = 글쓴이
                self.create_date = 생성날짜

        게시글1 = BlogFactory(
                '오늘 제주의 날씨',
                '오늘 제주의 날씨는 참 좋네요! 블라블라',
                '0',
                '이호준',
                '2023/05/10',
            )

        게시글2 = BlogFactory(
                '오늘 부산의 날씨',
                '오늘 부산의 날씨는 참 좋네요! 블라블라',
                '1000000',
                '김재현',
                '2023/05/10',
            )

        게시글3 = BlogFactory(
                '오늘 강원의 날씨',
                '오늘 강원의 날씨는 참 좋네요! 블라블라',
                '10000',
                '범남궁',
                '2023/05/10',
            )

        data = [게시글1, 게시글2, 게시글3]
        for i in data:
            if i.writer == '이호준':
                print(i.title)
                print(i.content)
                print(i.count)
                print(i.create_date)
        ```
* 클래스 상속
    * 클래스에서 상속은 상속해주는 클래스(Parent Class, Super class)의 내용(속성과 메소드)을 상속받는 클래스(Child class, sub class)가 가지게 되는 것
    * 코드 예
        ```python
        # 이 예제는 기억하고 있으셔야 합니다.
        class Car:
            maxSpeed = 300
            maxPeople = 5
            def move(self, x):
                print(x, '의 스피드로 달리고 있습니다.')
            def stop(self):
                print('멈췄습니다.')

        class HybridCar(Car):
            battery = 1000
            batteryKM = 300

        class ElectricCar(HybridCar):
            battery = 2000
            batteryKM = 600

        K3 = Car()
        HyK3 = HybridCar()
        ElHyK3 = ElectricCar()
        # id(K3.maxSpeed), id(HyK3.maxSpeed)
        # id(K3.move), id(HyK3.move)

        ElHyK3.move(10)
        ```