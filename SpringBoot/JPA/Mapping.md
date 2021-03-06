### 연관관계 매핑

#### 단방향 연관관계


연관관계에서는 `N:1 단방향` 관계를 먼저 이해해야 한다.


#### 객체 VS 테이블

+ 객체는 **참조(주소)** 로 연관관계를 맺는다.
+ 테이블은 **외래 키** 로 연관관계를 맺는다.


이 둘은 비슷하지만 다른 특징을 가진다.

연관 데이터를 조회할 떄, 객체는 `참조`를  테이블은 `조인`을 사용한다.




#### 양방향 연관관계

객체의 관점에서 바라봤을 때 서로 양방향이 되기 위해서는 각 객체에서 `참조`를 이뤄야 한다.

테이블에서 바라봤을 때  **외래 키** 하나로 양방향 조회가 가능하기 떄문에 처음부터 `양방향`이다.


엄밀히 말하자면 객체에서 `양방향` 이라는 것은 존재하지 않는다.

그저 `단방향 2개` 로 이루어진 것이 그렇게 보이는 것이다.



#### 연관관계의 주인 설정

`엔티티` 를 양방향으로 설정한다면 객체에서는 `참조`가 둘이 된다.

해당 연관관계의 주인을 설정해야한다.

이떄 연관관계의 주인은 **외래 키** 를 담당하고 관리할 수 있게된다.

그 반대관계는 그저 `읽기`만 가능하다.


그래서 **외래 키** 가 있는 곳을 연관관계의 주인으로 설정하는 것이 좋다.



#### 정리

`양방햘` 매핑은 복잡하다.

주인을 설정해야하고 `양방향`으로 만들기 위한 로직을 정리해야 하고, 

객체를 양쪽 방향으로 모두 관리해야 한다.

`양방향`은 주인이 아닌 연관관계를 추가한 것이며, `객체 그래프 탐색 기능(읽기 기능)` 이 추가 된 것에 불과하다.


**연관관계의 주인은 외래 키 위치와 관련해서 정하고, 비즈니스 중요도로 접근하지 말자**

