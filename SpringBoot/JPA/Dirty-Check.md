JPA로 엔티티를 수정할 떄 단순히 조회해서 데이터만 변경하면 된다.

트랜잭션 커밋 직전에 수정하는 기능을 써야하는 데 따로 없다.

사실 JPA는 `변경 감지` 기능을 사용해서 엔티티의 변화를 DB에 자동반영한다.

---

JPA는 영속성 컨텍스트에 엔티티를 보관할 때, 

최초 상태를 복사해서 저장해 두는데 이것을 `스냅샷` 이라고 한다.

그리고 플러시 시점에 스냅샷과 엔티티를 비교해서 변경된 엔티티를 찾는다.

 - 순서

1. 트랜잭션 커밋시 `EM` 내부에서 먼저 `flush`가 호출 된다.
2. 엔티티와 스냅샷을 비교해서 변경된 엔티티를 찾는다.
3. 변경된 엔티티가 있으면 쓰기 지연 저장소에 SQL을 보낸다.
4. 쓰기지연 저장소의 SQL을 DB로 전달한다.
5. DB 트랜잭션을 커밋을 한다.

`변경 감지` 는 영속성 컨텍스트가 관리하는 영속 상태의 엔티티만 적용된다.

그외 준영속, 비영속은 영속성 컨텍스트의 관리를 받지 못하는 것은 변경해도 

반영되지 않는다.

만약에 필드가 많거나 저장되는 내용이 너무 크면 수정된 데이터만 사용해서

동적으로 SQL을 생성하는 전략을 사용하자

```jsx
@DynamicUpdate
```

참고로 데이터를 저장할 때 데이터가 존재하는 (Not null field)필드만 

SQL을 생성하는 `@DynamicInsert` 도 있다.

---

- 엔티티 삭제

삭제시 대상 엔티티를 조회 해야한다.

삭제 대상 엔티티를 `em.remove()` 에 넘겨주면 된다.

물론 즉시 삭제가 아니라 엔티티 등록과 비슷하게 쓰기지연 저장소에 등록하고 

커밋해서 플러시를 호출하면 실제 DB에 쿼리를 전달한다.

`remove` 호출 순간 영속성컨텍스트에서 제거된다.
