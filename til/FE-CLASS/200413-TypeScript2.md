# 수업

- HTML 데이터 속성을 사용해서 데이터를 관리해보자
- 구현하는 것이 가장 중요하다
- API 구조 커뮤니케이션
- 백엔드 기술에 대해서 모르는 걸 많이 물어보기
- 데이터 베이스도 보여달라고 하고, 내 정보가 어떻게 처리되는지 계속 궁금해하고 물어보기
- **웹 개발에 대한 이해**
- HTTP에 대한 이해

## Typescript

### private fields

- private 키워드를 사용하지 않고 앞에 #을 붙이면 자동으로

### union 타입

- 여러 타입 허용

### 인터페이스

- 클래스를 사용한다면 인터페이스를 사용하기

## 학습 팁

- ...best practice / 최근 3개월 내용으로 검색해보기
- 구조가 어려우면 서버에게 데이터 구조가 어떻게 되어있는지 물어보기
- 싱글 페이지 어플리케이션의 핵심은 모델을 어떻게 관리하는가?
- 모델이 있고, 모델을 구독하는 뷰가 있어야 함
- 접기/펴기도 boolean 타입의 데이터가 있어야 함
- 모든 인터랙션과 화면의 변화는, 어떠한 상태의 변화에 의해서 바뀌는 것이 좋다
- **데이터가 바뀌면 화면이 바뀐다**
- 뷰는 더 바보가 돼야 한다. 모델이 변경되면 뷰가 바뀌게
- 하나의 모델 안에서 만들어보기
- 유니크한 id값을 키로 사용해도 된다

## 어떻게 좋은 데이터 구조를 가지는지

- data가 변경될 때 많은 부분이 변하는지
- 데이터 구조가 너무 중첩된 상태는 아닌지
- id로 쉽게 접근해서 찾을 수 있는지
- data normalization이란?

> 로딩 속도를 어떻게 해서든 줄이는 방법이 필요하다

- actionMap을 이용해서 key값을 사용해서 접근해서 사용할 수 있음
- MVC의 컨트롤러를 이런식으로 사용할 수도 있음

## 렌더링 최적화

> 지금 하려고 하지 말고 계속 의식하려고 노력하기

- 동일한 templating 작업이 일어나고 있지 않은지
- layout 생성이 단계적으로 생성되어 보이지 않는지
- 프리 패치
- 성능 개선이 즉 UX.. 사용자 경험
- 경험한 것들을 정리하고 어필하는게 굉장히 중요하다

## 나만의 라이브러리

1. 같은 서비스내에서 재사용할 수 있을까?
2. 내 다른 서비스에서도 사용할 수 있을까?
3. 전세계의 다른 개발자들도 사용할 수 있을까?

- 대신 이런식으로 사용하려면 제약조건이 필요하다.
- 쿼리 셀렉터말고, UI 컴포넌트 같은 걸 라이브러리로 만들어도 좋음

## 리뷰

- 이벤트 핸들러를 뷰와 너무 분리시켜 놓는 건 좋지 않다
- 웹팩 development, production 모드를 분리해서 사용하도록, URL 설정 파일을 따로 보관할 수 있음(서버 설정 파일)
- import 할 때`as name syntax` 사용해보기
- `dynamic import`, lazy-loading: 자바스크립트 파일이 클 경우, 초기로딩속도를 줄여준다
- 클래스명보다는 아이디를 쓰는게 좋다