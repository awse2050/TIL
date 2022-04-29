## React 이해

`React` 는 JS 라이브러리로 사용자 인터페이스를 만드는 데 사용한다.

구조가 `MVC` , `MVW` 등 프레임워크와 다르게 오로지 `뷰` 만 신경 쓰는 라이브러리이다.

`React` 에서는 특정 부분이 어떻게 생길지 정하는 선언체가 있는데, 이것을 `컴포넌트` 라 한다.

이것은 `템플릿` 과는 다른 개념인데, `컴포넌트`는 재사용이 가능한 `API` 로 수많은 기능을 내장하고 있으며, 

`컴포넌트` 하나에서 해당 `컴포넌트`의 생김새와 작동 방식을 정의합니다. 사용자 화면에 뷰를 보여주는 것을 `렌더링` 이라고 한다.

1.1 초기 렌더링

어떤 UI든 맨 처음에 어떻게 보여줄지 정하는 초기 렌더링이 필요하다.

`React` 에는 `render` 라는 함수가 있다. 

이 함수가 `컴포넌트` 의 생김새를 정의하는 역할을 한다.

`render` 를 통해서 그 내부에 있는 컴포넌트 들도 재귀적으로 렌더링하게 된다.

이렇게 최상위 `컴포넌트` 렌더링 작업이 끝나면 지니고 있는 정보들을 사용해서 HTML을 마크업하고

실제 페이지의 DOM 요소 안에 주입하게 된다.

1.2 조화 과정

`React`에서 뷰를 업데이트 할떄는 **업데이트 과정** 보다는 **조화 과정** 을 거친다고 하는 게 더 정확한 표현이다.  

`컴포넌트`에서 데이터에 변화가 있을 때 우리가 보기에 변화에 따라 뷰가 변형되는 것 처럼 보이지만, 사실은 새로운 요소를 갈아 끼우기 때문이다.

이 작업 또한 `render` 함수가 하며, `컴포넌트` 는 데이터를 업데이트 했을 때 단순히 업데이트한 값만 수정하는 것이 아니라 새로운 데이터를 가지고 `render` 함수를 다시 호출한다.

하지만, 이때의 `render` 함수는 결과를 바로 DOM에 반영하지 않고,

이전에 `render` 를 호출 했을 때 만들어진 `컴포넌트` 정보와 지금의 결과로 받은 `컴포넌트` 들을 비교하는데, 

JS를 이용해서 두 가지 뷰의 최소한의 연산으로 비교한 후 그 차이를 최소한의 연산으로  **DOM** 트리를 업데이트 한다.

전체 `컴포넌트` 를 처음부터 다시 렌더링하는 것 처럼 보이지만, 사실은 최적의 자원을 사용해서 이를 수행하는 것이다.

주요 특징은 가상의 DOM을 사용한다는 것이다.

1.3  DOM 이란?


객체로 문서 구조를 표현하는 방법으로 XML, 또는 HTML로 작성한다.

웹 브라우저는 DOM을 활용해 객체에 JS와 CSS를 적용하는데, DOM은 트리형태라서 특정 노드를 찾거나 수정하거나 제거하거나 원하는 곳에 삽입할 수 있다.

DOM 에는 치명적인 단점이 존재하는데, **바로 동적 UI에 최적화되어 있지 않다는 것이다.**

DOM 자체는 빠르고, DOM 자체를 읽고 쓸때 성능은 JS 객체를 처리할 때 성능과 비교하면

다르지 않지만, 웹 브라우저 단에서 DOM 변화가 일어나면 웹 브라우저가 다시 연산, 레이아웃 재구성, 등의 과정을 거치는데 이 과정에서 시간이 허비된다.

`React` 는 가상DOM 방식을 사용해 DOM 업데이트를 추상화함으로써 DOM 처리 횟수를 최소화하고 효율적으로 진행한다.