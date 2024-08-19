---
layout: post
permalink: /spring/boot0003/
categories: [spring]
related_posts:
  -
  - 
---

# Pagination


- [Spring 목차로 돌아가기] [1]

[1]: https://aminsc.github.io/spring/


## 페이지네이션
> 아마도 페이지 + 네비게이션으로 지어진 것 같다.

페이지 네이션은 주로 블로그에서 블로그 글들이 많을 경우, 이를 한 페이지에 몇 개의 게시글을 제공할 것인지 정의할 때 사용합니다.

### Page 인터페이스
Page<T> 인터페이스는 List<T>와 유사하게 데이터를 페이지 단위로 가져오도록 설계되었습니다. 
이 인터페이스는 페이징 된 데이터뿐만 아니라 페이징 정보를 함께 포함하여 제공하며, 
클라이언트(예: 웹 페이지)에서 `페이징 네비게이션`을 쉽게 구현할 수 있습니다.

### Page 주요 메서드

- `getContent()`:
페이징된 데이터 리스트를 반환합니다. List<T> 형태로 데이터를 가져올 수 있습니다.
예: List<MyEntity> content = myPage.getContent();


- `getTotalElements()`:
전체 데이터의 개수를 반환합니다.
예: long totalElements = myPage.getTotalElements();


- `getTotalPages()`:
전체 페이지 수를 반환합니다.
예: int totalPages = myPage.getTotalPages();


- `getNumber()`:
현재 페이지 번호(0부터 시작)를 반환합니다.
예: int pageNumber = myPage.getNumber();


- `getSize()`:
한 페이지에 포함된 요소 수를 반환합니다.
예: int pageSize = myPage.getSize();


- `hasNext()`:
다음 페이지가 존재하는지 여부를 반환합니다.
예: boolean hasNextPage = myPage.hasNext();


- `hasPrevious()`:
이전 페이지가 존재하는지 여부를 반환합니다.
예: boolean hasPreviousPage = myPage.hasPrevious();


- `isFirst()`:
현재 페이지가 첫 번째 페이지인지 여부를 반환합니다.
예: boolean isFirstPage = myPage.isFirst();


- `isLast()`:
현재 페이지가 마지막 페이지인지 여부를 반환합니다.
예: boolean isLastPage = myPage.isLast();


- `map(Function<? super T,? extends U> converter)`:
페이지의 각 요소를 다른 타입으로 변환할 때 사용합니다. 변환된 새로운 Page<U>를 반환합니다.
예: Page<DTO> dtoPage = myPage.map(entity -> new DTO(entity));

### Pageable 인터페이스
Pageable 인터페이스는 페이징 요청 정보를 캡슐화하는 데 사용됩니다. 
주로 PageRequest 클래스를 통해 구현됩니다.


### Pageable 주요 메서드
- `PageRequest.of(int page, int size)`:
특정 페이지를 요청할 때 사용합니다. 첫 번째 인자는 페이지 번호(0부터 시작), 두 번째 인자는 페이지 크기입니다.
예: Pageable pageable = PageRequest.of(0, 10);


- `PageRequest.of(int page, int size, Sort sort)`:
페이징과 함께 정렬 기준을 추가할 때 사용합니다.
예: Pageable pageable = PageRequest.of(0, 10, Sort.by("createdDate").descending());


### 사용 예시
블로그 페이지네이션 처리의 대한 간단한 예시입니다.

- 매개변수로 page, size를 받지만 기본 설정으로 0페이지부터 시작하며, 5개의 컨텐츠(게시글)를 제공한다고 정의하고 있습니다.
- 위에서 다뤘던 Page 인터페이스의 주여 메스드를 사용하였습니다.
  - getContent()를 사용하여 페이징된 데이터 리스트를 List 형태로 데이터를 다루기 위해 사용하였습니다.
  - getTotalPages()를 사용하여 전체 페이지 수를 제공합니다.
~~~java
//file: `Controller.java`

@GetMapping("/")
public String blogHome(Model model,
                      @RequestParam(value = "page", defaultValue = "0") int page,
                      @RequestParam(value = "size", defaultValue = "5") int size) {
    Page<Blog> blogPage = BlogService.getFindAllBlog(page, size);
    model.addAttribute("posts", blogPage.getContent());
    model.addAttribute("totalPages", blogPage.getTotalPages());
    model.addAttribute("currentPage", page);
    return "/blog/home";
}
~~~

- Pageable 인터페이스의 of() 메서드를 사용하여 특정 페이지를 요청하고 있습니다.
~~~java
//file: `Service.java`

// Read - All
@Override
public Page<Blog> getFindAllBlog(int page, int size) {
    Pageable pageable = PageRequest.of(page, size);
    return BlogRepository.findAll(pageable);
}
~~~

~~~java
//file: 'Reposioty.java'

Page<DiaTwoBlog> findAll(Pageable pageable);
~~~
