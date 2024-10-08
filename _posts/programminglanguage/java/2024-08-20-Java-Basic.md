---
layout: post
permalink: /java/basic01/
categories: [java]
related_posts:
  - 
  - 
---

# JavaBasic_01
## 자바 란

- [Java 목차로 돌아가기] [1]

  [1]: https://aminsc.github.io/java/

### 자바의 시작
자바 언어는 1991년 6월 셋톱 프로젝트를 위해 제임스 고슬링(James Gosling)이 만들었습니다. 
이 언어는 원래 제임스 고슬링의 사무실 밖에 있던 오크 나무를 따다 오크(Oak), 
혹은 그린(Green) 이라고 지으려했지만, 단어 리스트 중 무작위로 뽑은 자바(Java)를 선택했습니다. 

무작위로 뽑은 이름 치고는 개인적으로 이름이 촥촥 감긴다.<br>
{:.faded}

고슬링의 목표는 C/C++ 스타일의 언어와 가상 머신을 구현하는 것이었고, 
첫 공개 자바 버전은 1995년의 자바 1.0입니다. 
한 번 쓰고 어느 곳에도 실행 가능한 `Write Once, Run Anywhere`하는 것을 약속하였고 인기 플랫폼에 무료 런타임을 제공하였습니다.

> Write Once, Run Anywhere(한 번 작성하면 어느 플랫폼에서나 실행):
> 각 운영체제마다 자바를 사용하기 위해선 자바 가상 머신(JVM)이 있어야 하고, 
> 이 가상 머신 에서는 자바의 실행파일(.class)을 읽어 들일수 있기 때문입니다.

### 자바 특징
바로 위에서 언급한 WORA가, 자바는 플랫폼 독립적인 언어라는 것이 특징이라고 할 수 있습니다.
여기서 말하는 플랫폼 종속성과 독립성의 차이는, 실제로 컴퓨터가 읽는 코드를 작성하면
컴퓨터가 읽을 수 있는 바이트 코드는 운영체제와 CPU의 따라 각기 다릅니다.
예를 들어 맥에서 만들어진 실행파일(.app)을 윈도우(.exe)에서 사용할 수 없습니다.
하지만 자바의 경우 컴파일된 바이트 코드를 JVM 위에서 실행하기 때문에
서로 다른 플랫폼에서 작성된 자바 코드라도 플랫폼에 맞는 JVM만 있다면 실행이 가능하고 이를 플랫폼 독립성이라 합니다.



### 자바의 버전
자바의 버전은 보통 Java SE 또는 JDK/JRE의 버전으로 말합니다.
JDK(Java Development Kit)는 표준 라이브러리를 포함하며, 
JDK 버전이 바뀜에 따라 이 라이브러리가 확대되고 API가 바귑니다.

11버전 이전에는 JDK, JRE를 개별로 제공했으나 11버전부터 JRE를 포함한 JDK를 제공하여 더 편리해졌습니다.

자바의 버전은 6개월 주기로 나오고 있으며, LTS(Long Term Support)인 장기 지원 버전인 8, 11, 17, 21 버전이 있습니다.



### 자바의 철학
Java의 개발 철학은 아래 5가지 특정 목표를 중심으로 설계되어 있습니다.

1. 객체 지향 방법론
Java는 `객체 지향 프로그래밍(OOP)`에 기반을 둔 언어입니다. 
객체 지향 프로그래밍은 코드의 재사용성, 확장성, 유지보수성을 높이는 데 중점을 둡니다. 
Java는 클래스와 객체를 사용해 데이터를 캡슐화하고, 상속, 다형성, 추상화 등의 OOP 원칙을 따릅니다. 

2. 플랫폼 독립성
Java는 한 번 작성하면, 어디서든 실행할 수 있는(Write Once, Run Anywhere) 언어로 설계되었습니다.
Java 컴파일러는 Java 소스 코드를 바이트코드로 변환하며, 
이 바이트코드는 Java 가상 머신(JVM)이 설치된 모든 운영 체제에서 실행될 수 있습니다. 
이는 개발자가 동일한 코드베이스를 여러 플랫폼에서 사용할 수 있게 하여 개발 효율성을 크게 높입니다.

3. 네트워크 접근 기능의 기본 탑재
Java는 네트워크 프로그래밍을 쉽게 할 수 있도록 설계되었습니다. 
Java의 표준 라이브러리에는 소켓 프로그래밍, HTTP 통신, 원격 메소드 호출(RMI) 등의 네트워크 관련 기능이 기본적으로 포함되어 있습니다. 
이는 인터넷과 네트워크 애플리케이션의 개발을 용이하게 합니다. 

4. 안전한 원격 코드 실행
Java는 보안을 중요하게 생각하여, 특히 네트워크를 통해 전송되는 코드의 안전한 실행을 보장하기 위한 기능을 내장하고 있습니다. 
Java는 가상 머신의 샌드박스(sandbox) 환경에서 코드를 실행하며, 
애플릿(Applet)과 같은 원격 코드의 실행 시 보안 매니저(Security Manager)를 통해 권한을 제한할 수 있습니다. 
이는 외부에서 들어오는 악성 코드를 방지하여 시스템을 보호합니다.

5. 편리한 객체 지향 언어
Java는 C++ 등 기존 객체 지향 언어들의 장점을 취하면서도, 
복잡성을 줄이고 사용성을 높이기 위해 노력했습니다. 
Java는 메모리 관리를 자동으로 해주는 가비지 컬렉터(Garbage Collector)를 제공하여, 
개발자가 메모리 관리를 직접하지 않도록 했습니다. 
또한 포인터와 같은 복잡한 기능을 제거하여, 프로그래밍의 안정성과 생산성을 높였습니다.
예를 들어, C++에서는 메모리 누수를 방지하기 위해 개발자가 직접 메모리 해제를 관리해야 하지만, 
Java에서는 가비지 컬렉터가 자동으로 메모리를 관리합니다.
