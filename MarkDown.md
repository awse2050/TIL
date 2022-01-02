1.  제목

`<h1>` 부터 `<h6>` 까지 제목을 표현할 수 있다.

```jsx
# 제목1
## 제목2
### 제목3
#### 제목4
##### 제목5
###### 제목6
```

제목1과 제목2는 다음과 같이 표현할 수 있다.

```jsx
제목 1
=======

제목 2
-------
```

2. 강조하기

각각 `em`,  `strong` , `del` 태그로 변환된다.

밑줄을 입력하고 싶다면 `u` 태그를 사용할 것.

```jsx
기울기는 *별표* 또는 _언더바_를 사용할 것
두껍게 사용할 경우 **별표**, __언더바__
취소선은 ~~물결표~~
```

3. 목록

`ol` , `ul` 태그를 반환한다.

```jsx
-순서가 필요하지 않는 목록에 사용 가능한 기호
 - 대쉬
 * 별표
 + 더하기
```

4. 링크

```jsx
[GOOGLE](https://google.com)
=> GOOGLE

[NAVER](https://naver.com "링크 설명(title)을 입력하세요.")

[상대적 참조](../users/login)

```

5. 이미지

`img` 로 변환된다.

링크와 비슷하지만 앞에 `!` 가 붙는다.

```jsx
![대체 텍스트를 입력하세요](url)
```

5-1  이미지에 링크걸기

마크다운 이미지 코드를 링크코드로 묶는다.

```jsx
[![Vue](/images/vue.png)](https://kr.vuejs.org/)
```

6. 코드 강조

`pre` , `code` 로 변환된다.

숫자 1번키 왼쪽의 `(Grave)를 입력하라.

7. 블록 코드 강조

Grave를 연속 3번 입력 후 코드 종류도 적는다.


``` html
<a></a>
```

```css
.list > li {
  position: absolute;
  top: 40px;
}
```

```javascript
function func() {
  var a = 'AAA';
  return a;
}
```

```bash
$ vim ./~zshrc
```

```python
s = "Python syntax highlighting"
print s
```


8. 표 (table)

`table` 태그로 변환된다.

헤더 셀을 구분 시 3개이상의 `-` 기호가 필요하다.

헤더 셀을 구분하면서 `:` 기호로 셀 안에 내용을 정렬가능

가장 좌측과 우측에 있는 `|` 기호는 생략 가능


| 값 | 의미 | 기본값 |
|---|:---:|---:|
| `static` | 유형(기준) 없음 / 배치 불가능 | `static` |
| `relative` | 요소 자신을 기준으로 배치 |  |
| `absolute` | 위치 상 부모(조상)요소를 기준으로 배치 |  |
| `fixed` | 브라우저 창을 기준으로 배치 |  |

값 | 의미 | 기본값
---|:---:|---:
`static` | 유형(기준) 없음 / 배치 불가능 | `static`
`relative` | 요소 **자신**을 기준으로 배치 |
`absolute` | 위치 상 **_부모_(조상)요소**를 기준으로 배치 |
`fixed` | **브라우저 창**을 기준으로 배치 |


9. 인용문

`blockquote` 태그로 변환된다


인용문(blockQuote)

> 남의 말이나 글에서 직접 또는 간접으로 따온 문장.
> _(네이버 국어 사전)_

BREAK!

> 인용문을 작성하세요!
>> 중첩된 인용문(nested blockquote)을 만들 수 있습니다.

>>> 중중첩된 인용문 1

>>> 중중첩된 인용문 2

>>> 중중첩된 인용문 3


10. 수평선

각  기호를 3번 입력하세요

```jsx
---  대쉬 3번

*** 별표 3번

____ 언더바 3번
```

11. 줄바꿈하기

`br` 태그를 직접 쓰거나 2번 띄어쓰기를 하라,.
