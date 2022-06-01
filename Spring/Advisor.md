## Advisor

- **포인트컷(PointCut)** : 어디에 부가 기능을 적용할지, 어디에 부가 기능을 적용하지 않을지 판단하는 **필터링 로직**이다. 주로 클래스와 메서드 이름으로 **필터링**을 한다. 이름 그대로 어떤 포인트에 기능을 적용할지 하지 않을 지 잘라서 구분하는 것이다.
- **어드바이스(Advice)** : 이전에 본 것처럼 프록시가 호출하는 **부가 기능**이다. 단순하게 프록시 로직이라 생각하면 된다.
- **어드바이저(Advisor)** : 단순하게 **하나의 포인트컷과 하나의 어드바이스**를 가지고 있는 것이다.

즉, 부가 기능 로직을 적용하는데, **포인트컷(PointCut)** 으로 어디에 적용할지 선택하고, 
**어드바이스(Advice)** 로 어떤 부가 기능을 적용할지 선택하는 것이다.

그리고 어디에 어떤 로직을 적용할지 알고 있는 것을 **어드바이저**라고 한다.


---


### 스프링이 제공하는 포인트컷

- `NameMatchMethodPointcut` : 메서드 이름을 기반으로 매칭한다. 내부에서는 `PatternMatchUtils` 를 사용한다.
    - 예)  `*xxx*` 를 허용한다.
- `JdkRegexpMethodPointcut` : JDK 정규 표현식을 기반으로 포인트컷을 매칭
- `TruePointcut` : 항상 참을 반환한다.
- `AnnotationMatchingPointcut` : 애노테이션으로 매칭한다.
- `AspectJExpressPointcut` : aspectJ 표현식으로 매칭한다.

**가장 중요한 것은 aspectJ 표현식이다.**

실무에서는 사용하기도 편리하고 기능도 많은 `aspectJ` 표현식을 기반으로 

`AspectJExpressPointcut` 을 사용하게 된다.

---

### 중요

**스프링 AOP**를 처음 공부하거나 사용하면, **AOP적용 수 만큼 프록시가 생성된다고 착각**하게 된다. 

실제로 많은 실무 개발자들도 그렇게 생각하는 사람이 있었다.

스프링은 AOP를 적용할 때, 최적화를 진행해서 지금처럼 프록시를 하나만 만들고, 

하나의 프록시에 여러 어드바이저를 적용한다.

**즉, 여러개의 어드바이저를 적용해도 하나의 프록시만을 이용한다는 것이다.**