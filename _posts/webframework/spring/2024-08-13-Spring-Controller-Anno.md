---
layout: post
permalink: /spring/anno0001/
categories: [spring]
related_posts:
  -
  - 
---

# Controller Annotation @Controller vs @RestController


- 목차로 돌아가기[spring] [1]

[1]: https://aminsc.github.io/pl/spring/


#### @Controller
- 개인적으로 Monolithic으로 반환값은 `String`타입을 주로 사용하며, 반환값에 Templates 경로를 넣어줍니다. 따라서 SSR(Server Side Rendering)으로 생각되며 자세한 작동 원리는 좀 더 알아본 뒤 보강 하거나 따로 다뤄보겠습니다.

#### @RestController
- @Controller와 상반되는 MSA(MicroService Architecture)로 반환값은 데이터와 Status Code가 주입니다. 따라서 API로 데이터(객체)를 제공하여 CSR(Client Side Rendering)로 생각되지만 이것 또한 같이 알아본 뒤 보강 하거나 따로 다뤄보겠습니다.
