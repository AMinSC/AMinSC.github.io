---
layout: post
permalink: /spring/boot0004/
categories: [spring]
related_posts:
  -
  - 
---

# ManyToMany, JoinTable Annotation


- [Spring 목차로 돌아가기] [1]

[1]: https://aminsc.github.io/spring/


## @ManyToMany 및 @JoinTable 어노테이션
해당 어노테이션은 예를 들어 게시글과 태그, 혹은 카테고리 처럼 다대다 관계를 정의할 때 사용하게 되었습니다.

Spring Data JPA에서 @ManyToMany 관계를 설정할 때, 중간 테이블이 필요하게 됩니다. 
이 중간 테이블을 "조인 테이블"이라고 하며, 두 엔티티 간의 다대다 관계를 매핑하기 위해 사용됩니다.

이 조인 테이블을 Spring Data JPA가 자동으로 생성하며, 
명시적으로 엔티티 클래스로 정의하지 않더라도 Hibernate가 이를 관리하고 필요한 경우 생성합니다. 
@ManyToMany 어노테이션을 사용해 A Table(Blog)와 B Table(Category) 간의 관계를 설정했기 때문에, 
Hibernate는 두 엔티티 간의 매핑을 처리하기 위해 중간 테이블을 생성합니다.


### @ManyToMany 및 @JoinTable 어노테이션
@ManyToMany와 @JoinTable 어노테이션은 JPA(Java Persistence API)에서 
엔티티 간의 다대다(Many-to-Many) 관계를 설정하는 데 사용됩니다. 
이 두 어노테이션은 다대다 관계의 매핑을 정의하고, 관계를 관리하는 조인 테이블을 생성하는 데 중요한 역할을 합니다.


### @ManyToMany 어노테이션
@ManyToMany 어노테이션은 엔티티 간의 다대다 관계를 나타내는 데 사용됩니다. 
예를 들어, 블로그와 카테고리 간의 관계를 생각해볼 수 있습니다. 
하나의 블로그는 여러 카테고리에 속할 수 있고, 하나의 카테고리도 여러 블로그에 속할 수 있습니다. 
이런 관계는 다대다 관계라고 부릅니다.


### @JoinTable 어노테이션
@JoinTable 어노테이션은 다대다 관계를 관리하는 데 사용되는 조인 테이블을 명시적으로 
정의하는 데 사용됩니다. 이 조인 테이블은 두 엔티티 간의 관계를 매핑하는 데 사용됩니다. 만약 @JoinTable을 명시적으로 지정하지 않으면, JPA는 기본값을 사용하여 테이블을 생성합니다.



### 사용 예시
- 속성 설명
  - `name`: 생성될 조인 테이블의 이름을 지정합니다. 이 예시에서는 blog_category라는 테이블이 생성됩니다.

  - `joinColumns`: 현재 엔티티(Blog)의 외래 키를 나타내는 @JoinColumn을 정의합니다. 여기서는 blog_id라는 이름의 컬럼이 생성됩니다.

  - `inverseJoinColumns`: 연관된 엔티티(Category)의 외래 키를 나타내는 @JoinColumn을 정의합니다. 여기서는 category_id라는 이름의 컬럼이 생성됩니다.
~~~java
//file: 'Blog.class'

@Entity
public class Blog {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String title;

    @ManyToMany
    @JoinTable(
        name = "blog_category",
        joinColumns = @JoinColumn(name = "blog_id"),
        inverseJoinColumns = @JoinColumn(name = "category_id")
    )
    private Set<Category> categories = new HashSet<>();

    // 기타 필드 및 메서드
}
~~~

- 속성 설명
  - `mappedBy`:  @ManyToMany 관계에서 양방향 매핑을 설정할 때, 한쪽 엔티티에 mappedBy 속성을 사용하여 관계의 주인이 아닌 것을 표시합니다. 예를 들어, Category 엔티티의 blogs 필드에 mappedBy = "categories"를 설정하여 Blog 엔티티의 categories 필드가 관계의 주인임을 나타냅니다.
~~~java
//file: 'Category.class'

@Entity
public class Category {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @ManyToMany(mappedBy = "categories")
    private Set<Blog> blogs = new HashSet<>();

    // 기타 필드 및 메서드
}

~~~

### 매핑의 동작 원리
1. `엔티티 저장`: Blog 또는 Category 객체를 저장할 때, JPA는 이들 간의 관계를 조인 테이블(blog_category)에 삽입합니다. 예를 들어, 하나의 블로그가 세 개의 카테고리에 속한다면, 조인 테이블에 세 개의 행이 삽입됩니다.

2. `엔티티 조회`: 블로그를 조회할 때, 관련된 카테고리들을 로드할 수 있습니다. 이 경우, 조인 테이블을 사용해 블로그와 카테고리 간의 관계가 해결됩니다.

3. `엔티티 삭제`: 엔티티를 삭제할 때, 조인 테이블에 있는 관련된 행들도 함께 삭제됩니다. 이를 위해 cascade 속성을 적절하게 설정해야 합니다.
