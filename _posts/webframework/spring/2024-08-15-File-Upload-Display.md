---
layout: post
permalink: /spring/boot0002/
categories: [spring]
related_posts:
  -
  - 
---

# File(Image) Upload and Display


- [Spring 목차로 돌아가기] [1]

[1]: https://aminsc.github.io/spring/


## 이미지 업로드, 디스플레이
이번에 미니 프로젝트를 진행하면서 게시판을 작성할 때 이미지를 첨부하여 저장하고, 전체 게시글을 제공하는 페이지와 게시글 상세페이지에서 이미지를 제공하고 싶었습니다.

### 클라이언트
클라이언트 단에서는 간단하게 HTTP method와 HTTP request, Type을 설정해 줬습니다.

~~~html
<form th:action="@{/api/endpoint}" method="post" enctype="multipart/form-data">
<!--    다른 컨텐츠 들-->
    <div>
        <label for="img" class="form-label">Upload Image</label>
        <input class="form-control" type="file" id="img" name="img" accept="image/*">
    </div>
</form>
~~~
> `th:` 는 thymeleaf문법입니다.
- `th:action`: 서버단에서 정의한 엔드포인트를 명시하는 곳으로, 저는 위에 모든 코드를 작성하진 않았지만, 게시글을 작성하기 때문에 서버의 게시글 생성 엔드포인트를 설정해 줬습니다.
- `method`: HTTP의 메서드를 명시하는 곳으로, 보통 생성하는 요청은 POST를 사용합니다.
- `enctype`: 전송하는 데이터의 인코딩 속성을 명시하는 곳으로, 보통 POST에서는 `application/x-www-form-urlcencoded`을 주로 사용하지만, 파일(이미지)을 전송하기 때문에 `multipart/form-data`를 작성했습니다.
- `accept`: 전송하는 파일의 타입을 명시하는 곳으로, `type`이 file일 경우 사용되며, image를 제외한 audio, video 등이 있습니다. /(슬러시) 뒤 쪽은 확장자를 명시합니다.

### 서버
동적 타입의 언어를 사용하다가 정적 타입의 언어를 사용하다 보니 Django보다 상대적으로 신경 쓸 것이 많았습니다.
따라서 첨부파일을 받을 때 어떤 타입으로 매개변수를 받아야 될지 고민이었습니다.

서버단에서는 클라이언트에서 제공한 데이터를 원하는 방식으로 핸들링할 수 있으며, 
저는 이미지를 저장하고 표시하는 기능을 구현하고 싶어서 매개변수를 `MultipartFile`타입으로 받았습니다.

1. `MultipartFile`타입으로 이미지를 매개변수로 받습니다.
2. 받은 이미지를 저장할 경로를 명시해 줍니다. (절대경로)
3. (선택사항) 파일관리를 위하여 서비스 별, 일자 별로 관리하는 로직을 추가합니다.
4. (선택사항) 중복된 파일 이름을 보완하기 위해 uuid를 사용하여 파일 이름에 추가합니다.
5. `File` 클래스를 활용하여 (2) ~ (4)에서 명시한 경로를 인수로 넣어 파일 객체를 생성합니다.
6. `MultipartFile`의 transferTo 메서드를 활용하여 파일 객체의 경로에 클라이언트에서 전달받은 실제 이미지를 저장합니다.
7. 데이터베이스에 파일 이름과 경로를 저장합니다.

> 추가적으로 파일 크기를 최적화하는 로직을 추가할 수 있습니다.


## 새로 사용한 Java API
이번 Spring Boot 미니 프로젝트에서 이미지를 업로드 기능을 다룰 때 매개변수로 [`MultipartFile`](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/multipart/MultipartFile.html#transferTo(java.io.File)) 인터페이스를 사용했습니다.

사용 메서드로는 [`transferTo`](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/multipart/MultipartFile.html#transferTo(java.io.File))를 사용하여 이미지를 경로에 저장했습니다.

