### Proxy Pattern


`클라이언트` 와 `서버` 라고 하면 개발자들은 보통 서버 컴퓨터를 생각한다.

사실 `클라이언트` 와 `서버` 의 개념은 상당히 넓게 사용된다. `클라이언트` 는 의뢰인 이라는 뜻이고, `서버` 는 서비스나 상품을 제공하는 사람이나 물건을 뜻한다.

따라서 `클라이언트` 와 `서버`의 기본 개념을 정의하면 

**클라이언트는 서버에 필요한 것을 요청하고, 서버는 클라이언트 요청을 처리하는 것이다.**


`클라이언트` 가 요청한 결과를 `서버` 에 직접요청하는 것이 아니라, 어떤 대리자를 통해서 대신 간접적으로 `서버`에 요청할 수 있다. 

예를 들어, 내가 직접 장을 볼수 있지만 누군가에게 대신 장을 봐달라고 부탁할 수 있다.

여기서 **대신 장을 보는 대리자를 영어로 프록시라고 한다.**

그리고 프록시는 중간에 여러가지 일을 추가로 할 수 도 있다.

1. 라면 구매를 요청했으나, 라면이 집에 있는 경우 기대한 것보다 빨리 먹을 수 있음.
2. 자동차 주유를 부탁했으나 추가로 세차까지 하게되었음. 따라서 기대한 것 보다 추가적인 결과를 얻음.
3. 대리자가 또 다른 대리자를 부를 수 있다. 중요한 점은 내가 부른 대리자를 통해서 결과를 받을 수 있기만 하면 된다.


---

**대체 가능**

여기까지 보면 아무 객체나 `프록시`가 될수 있을 것 같지만, 아니다

객체에서 프록시가 되려면, 클라이언트는 서버에게 요청한 것 인지, `프록시`에게 요청한 것인지 조차 몰라야 한다.

쉽게 얘기하여 서버와 프록시는 같은 인터페이스를 사용해야한다, 그리고 클라이언트가 사용하는 서버 객체를 프록시 객체로 변경해도 클라이언트 코드를 변경하지 않고 동작할 수 있어야 한다.


클라이언트가 서버 인터페이스에만 의존한다. 그리고 서버와 프록시가 같은 인터페이스를 사용하여 DI를 사용해서 대체가 가능해진다.


런타임에 클라이언트 객체에 `DI` 를 사용해서 Client → Server 에서 Client → Proxy 로 객체 의존관계를 변경해도 클라이언트 코드를 변경하지 않아도 된다. 

클라이언트 입장에서는 변경 사실 조차 모른다.

`DI` 를 사용하면 클라이언트 코드 변경없이 유연하게 프록시를 주입할 수 있다.


---

### 프록시의 주요기능

1. **접근 제어**
    1. 권한에 따른 접근 차단
    2. 캐싱
    3. 지연 로딩
2. **부가 기능 추가**
    1. 요청 값이나, 응답 값을 중간에 변형한다.
    2. 실행 시간을 측정해서 추가 로그를 남긴다.

프록시 객체가 중간에 있으면 크게 **접근 제어**와 **부가 기능 추가**를 수행할 수 있다.

GOF 디자인 패턴에서 `의도` 에 따라서 프록시 패턴과 데코레이터 패턴으로 구분한다.

- **프록시 패턴** : 접근 제어가 목적
- **데코레이터 패턴** : 새로운 기능 추가 목적

둘다 `프록시`를 사용하지만, `의도`가 다르다는 점이 핵심이다. 

용어가 프록시 패턴이라고 해서 이 패턴만 `프록시`를 사용하는 게아니라 데코레이터 패턴 또한 `프록시`를 사용한다.

 **프록시 ≠ 프록시 패턴**