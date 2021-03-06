
리터럴은 소스 코드상에 `고정값`을 의미하는 용어이다.

예를 들어, `Hello` 는 `문자 리터럴` , `10`, `20` 은 `숫자 리터럴` 이다.


타임리프에서는 기본적으로 `문자 리터럴`은 항상 `'` 로 감싸서 사용해야 한다.

```html
<span th:text="'hello'"></span>
```

그런데 항상 `'` 을 사용해서 문자를 감싸는 것은 귀찮은 작업으로 간주된다.

따라서 공백 없이 만들어낸 리터럴은 하나의 토큰으로 인지해서 다음과 같이 생략하여 쓸 수 있다.

```html
<span th:text="hello"></span>
```


대신, 이러한 `문자 리터럴` 사이에 공백이 존재한다면 오류를 발생시킨다.


```html
<span th:text="hello Thymeleaf!"></span>
```

그래서 이 템플릿을 조금 더 편리하게 사용할 수 있도록 지원하는 문법이 있다 

키보드 P 오른쪽에 `|`(수직선 바) 기호를 사용해서 감싼다면 `'` 필요없이 사용이 가능하다

```html
<span th:text="|hello Thymeleaf!|"></span>

<span th:text="|hello ${data}|"></span>

```
