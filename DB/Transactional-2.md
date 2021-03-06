### 트랜잭션 개념 이해 2

**DB 연결 구조 및 DB 세션**

- **사용자**는 **WAS**나 **DB 접근 툴** 같은 클라이언트를 사용해서 DB 서버에 접근할 수 있다. 클라이언트는 DB서버에 연결을 요청하고 **커넥션을** 맺게된다. 이 때 DB서버는 내부에 **세션**이라는 것을 만든다. 그리고 **앞으로 해당 커넥션의 모든 요청은 이 세션을 통해서 실행**하게 된다.
- 쉽게 말해 개발자가 클라이언트를 통해 `SQL` 을 전달하면 현재 **커넥션**에 연결된 세션이 `SQL` 을 실행한다.
- 세션은 **트랜잭션**을 시작하고, `Commit` , `Rollback` 을 통해 **트랜잭션**을 종료한다. 그리고 이후에 새로운 **트랜잭션**을 다시 시작 할 수 있다.
- 사용자가 **커넥션**을 닫거나, DBA가 세션을 강제로 종료하면 세션은 종료된다.

---

**트랜잭션 사용법**

- 데이터 변경 쿼리를 실행하고 DB에 그 결과를 반영하려면 커밋 명령어인 `commit` 을 호출하고, 결과를 반영하고 싶지 않으면 롤백 명령어인 `rollback` 을 호출하면 된다.
- **커밋을 호출하기 전까지는 임시로 데이터를 저장**하는 것이다. 따라서 해당 **트랜잭션**을 시작한 **세션**(사용자)에게만 변경 데이터가 보이고 다른 **세션**(사용자) 에게는 변경 데이터가 보이지 않는다.
- **등록, 수정, 삭제 모두 같은 원리로 동작한다.**


**커밋하지 않은 데이터를 다른 곳에서 조회할 수 있으면 어떤 문제가 발생할까**

- 예를 들어, **커밋하지 않는 데이터**가 보인다면, **세션2**는 데이터를 조회했을 때 **회원1, 2**가 보일 것이다. 

- 따라서 **회원1, 2**가 있다고 가정하고 어떤 로직을 수행할 수 있다. 그런데 **세션1**이 롤백을 수행하면 **회원1, 2**의 데이터가 사라지게 된다. 따라서 **데이터 정합성 문제**가 발생한다.


---

### 자동 커밋, 수동 커밋

**자동 커밋**

`트랜잭션` 을 사용하려면 **자동 커밋** 과 **수동 커밋**을 이해해야 한다.

**자동 커밋**으로 설정하면 각각의 쿼리를 실행 직후 자동으로 커밋을 호출한다.

따라서 커밋이나 롤백을 직접 호출하지 않아도 되는 편리함이 있다.

하지만 쿼리를 하나하나 실행할 때 마다 자동으로 커밋이 되어버리기 때문에 우리가 원하는 트랜잭션 기능을 제대로 사용할 수 없다.

**자동 커밋 설정**

```jsx
set autocommit true; //자동 커밋 모드 설정
insert into member(member_id, money) values ('data1',10000); //자동 커밋
insert into member(member_id, money) values ('data2',10000); //자동 커
```

따라서 `Commit` , `Rollback` 을 직접호출하면서 트랜잭션 기능을 제대로 수행하려면 **자동 커밋**을 끄고 **수동 커밋**을 사용해야 한다.

**수동 커밋 설정**

```jsx
set autocommit false; //수동 커밋 모드 설정
insert into member(member_id, money) values ('data3',10000);
insert into member(member_id, money) values ('data4',10000);
commit; //수동 커밋
```

보통 **자동 커밋 모드**가 기본적으로 설정된 경우가 많기 때문에, **수동 커밋 모드로 설정하는 것을 트랜잭션을 시작한다고 표현**할 수 있다.

수동 커밋 설정을 하면 이후에 꼭 `Commit` , `Rollback` 을 호출해야 한다.

참고로 **수동 커밋 모드**나 **자동 커밋 모드**는 한번 설정하면 해당 세션에서는 계속 유지된다. 중간에 변경하는 것은 가능하다 

⇒ 트랜잭션이 시작되면 하나의 세션과 커넥션이 연결된 상태로 작업이 이루어지기 때문에 다른 세션에서는 변경사항을 직접 `Commit` 하지 않는 이상 보이지 않는다.


---


**정리**

**원자성 :** 트랜잭션 내에서 실행한 작업들은 마치 하나의 작업인 것 처럼 모두 성공하거나 모두 실패해야한다. 트랜잭션의 원자성 덕분에 `SQL` 명령어를 하나의 작업인 첫처럼 처리할 수 있다.

**오토 커밋** : 만약 오토 커밋 모드로 동작하는데, 계좌이체가 중간에 실패한다면 하나의 `SQL` 을 실행할 때마다 커밋이 되기 때문에 특정 인원의 금액만 줄어드는 상황이 발생 할 수 있다.

**트랜잭션 시작** : 이런 종류의 작업은 꼭 **수동 커밋 모드**를 사용해서 수동으로 **커밋, 롤백**을 할수 있도록 해야한다. 보통 이렇게 **자동커밋 모드**를 수동으로 전환하는 것을 트랜잭션을 시작한다고 표현한다.
