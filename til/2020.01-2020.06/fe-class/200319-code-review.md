# 자판기 코드 리뷰

* Develop 브랜치는 테스트 코드를 없애는 연습
* 디렉토리 이름은 확실하게
* CSS 파일도 컴포넌트별로 분리할 수 있다.
  * **파일이 하나면**, 변경될 때마다 계속 큰 파일을 새로 다운로드 받아야 함 -&gt; 캐시가 잘 안된다.
  * **파일이 여러개면**, HTTP Request가 많아진다.
  * static 파일을 캐시해서 저장한다. 헤더에 캐시를 할 지 말 지, 언제까지 저장할지 정할 수 있다.
  * 브라우저가 캐시한다는 뜻은 요청이 서버로 안간다는 뜻
  * HTTP 2.0 을 공부하기. 역사를 따라서
* 파일이 하나일 때, 여러가지일 때 비슷하기 때문에, 상황에 따라 적절하게 파일을 나누는 게 좋다.
* 빌드 배포 자동화: 문제가 생길 경우 긴급 인력이 따로 투입되지 않아도 해결될 수 있게 배포 과정을 자동화하기
* **내 일상 속 작은 문제부터 자동화해보기. 내 문제를 개선하는 습관.**
  * 프론트엔드 개발자니까 JS만? 절대 아니다.
  * 파이썬도 공부해보고, 쉘 스크립트도 공부해보고
  * 좋은 개발자의 모습.

## 디렉토리 구조 예시

```text
/js
  view
    menu.js
  controller
    a.js

/css
  common
    lib(vendor) : 외부 라이브러리
      reset.css
    font.css
    layout.css
  page
    a.css
    b.css
```

## 코드 상세 리뷰

* 개발할 때 주석으로 역할을 정의해놓고 짜는 것도 좋은 방법
* 이벤트 리스너 내부의 콜백 함수는 개별 함수로 빼서 사용하기. 예\) `Button.addEventListener("click", buttonClickHandler)`
* 로직에 의미없는 상수들은 파일에서 빼버리거나 모듈화하기. `config`라는 네임스페이스 만들어서 변수화하기.
* 디렉토리명, 변수명, 함수명 항상 신경쓰기
* `진짜진짜최종` 파일 관리하듯 주석 달고, 파일을 관리하지 말기. **개발자는 `Git`을 믿고 `Git`으로 버전 관리하기.**
* 서브루틴을 잘 나누고 함수 호출관계를 잘 이해하기

### 초기화를 어떻게 할 것인가

```javascript
//1
const wm = new WalletModel();
//2
const wm = new WalletModel(); // 객체만 생성
wm.initailize({FIRST_DATA_URL: DATA.FIRST_URL}); // 초기데이터 가져오기
```

* 이벤트를 발생시킨다: `dispatch()` \(최근 쓰는 이름\)
  * `fireEvent()` \(예전\)
* `hasOwnProperty` : 알아보면 좋다
* 템플릿 리터럴을 반복문으로 할 수 있지 않을까?
  * `template literal iteration`
* 생성자에 내용이 없으면 클래스 내라도 constructor\(\)를 굳이 쓰지 않아도 괜찮다.

### 즉시실행함수

* 전역공간을 오염시키지 않기 위해 사용한다.
* ES Module에서 필요한지는 생각할 필요가 있다.
* 클래스를 대신해서 사용할 수도 있다.
* 외부 라이브러리들이 서비스와 충돌하지 않기 위해 사용
* scope를 감싸주는 전략. zero global 전략
* 자바스크립트 모듈패턴: 클래스와 es module이 없을 때, 즉시실행함수 내부에서 public으로 사용하고 싶은 요소들만 객체로 리턴해서 사용
* set과 array의 차이?
* arrow function은 bind를 쓸 필요가 없다
* 내 util을 만들어서 계속 쓰기 -&gt; 나만의 라이브러리를 만들어가는 경험

```text
this.vendingMachineModel.subscribe({
  type: "UPDATE_CASH",
  callback: this.updateCash();
})
```

* 인자를 주고 받을 때 대화하듯 키 밸류로 전달해주는 방식 좋다.
* 코드에서 HTML 구조를 포함하면 취약한 구조가 될 수 있다.
* `Object.freeze`
* 자바스크립트 엔진이 빠르다보니, 무의미한 반복문을 여러번 돌 수도 있다. 똑같은 행동을 안하게 만들기
* CSS 조작은 클래스명으로 접근하기. ClassList로 접근하고, toggle을 활용하기
* 서버에 업데이트를 언젠가는 해줘야함. 새로고침해도 데이터가 남아있을 수 있게

