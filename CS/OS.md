## 운영체제 (Operation System)

`운영체제` 란 컴퓨터 하드웨어 윗단에 설치되는 **소프트웨어** 이다.

`시스템`이라는 용어는 주로 기반이나 틀이되는 **하드웨어**를 지징할 때 주로 사용되는데,

**소프트웨어**인 운영체제에 시스템이라는 용어가 사용된 것은 **하드웨어**와 **운영체제**가 같이쓰여야만 하기 때문이다.

컴퓨터 전원을 켤 때 **운영체제**가 없으면 동작하지않는다. 컴퓨터를 동작하게 하기 위한 기본적인 **소프트웨어**가 바로 **운영체제**이다

**운영체제**는 하나의 **소프트웨어**로써 컴퓨터 전원이 켜지면 메모리가 올라가는데, 이렇게 큰 **운영체제**라는 프로그램이 모두 메모리에 올라가면

한정된 메모리 공간의 낭비가 심해지므로 필요한 부분만 메모리에 올리고 나머지 부분은 필요할 때 올려서 사용한다.

---

### 운영체제의 기능

`운영체제`는 하드웨어와 사용자 사이에 존재하므로 운영체제의 역할은크게 2가지로 나뉜다.

**1. 하드웨어를 위한 역할**

**2. 사용자를 위한 역할**

하드웨어 쪽에서 사용자가 다루기 힘든 부분을 관리하는 역할을 하며, 자세하게는 **컴퓨터 시스템 내의 자원을 효율적으로 관리하는 역할**이다.

사용자에게는 **편리한 인터페이스를 제공**한다. 마치 각각의 사용자가 독자적으로 컴퓨터를 쓰는 것과 같은 느낌을 제공하는 역할이다.

예를 들어, 사용자가 파일을 저장할 때 디스크에 어떻게 저장되고는 몰라도 된다. **운영체제**가 알아서 파일을 저장할 때 과정을 거쳐서 제공해줄 뿐이다.


**중요한 핵심기능**은 **결국 컴퓨터 시스템 내의 자원을 효율적으로 관리하는 역할을 한다는 것**이다. 

여기서 자원은 **하드웨어 및 소프트웨어의 자원**을 전부 통틀어서 지칭하는 단어이다.

그래서 자원들을 효율적으로 관리하여 가장 최고의 성능을 뽑아내야하는데, 전체적인 성능을 향상시키려다 보면 일부 프로그램이나 사용자가 불이익을 당할 떄가 있기도 하다.

따라서, **형평성있게 자원이 분배되도록 하는 역할**이 필요로 하다.


이밖에 각각의 사용자 프로그램이 서로에게 영향을 미치면 안된다는 점이 존재한다.

---

### 운영체제의 분류

#### 동시 작업 여부에 따른 분류

- **단일작업용 운영체제** 

한번에 하나의 프로그램만 실행시킬 수 있다.

- **다중작업용 운영체제** 

동시에 2개 이상의 프로그램을 처리할 수 있다.

**다중작업용 운영체제**는 여러 프로그램이 `CPU`와 메모리를 공유하게 된다. 비록 하나밖에 없어서 처리의 최대 개수가 1개의 프로그램 뿐이더라도

`CPU` 처리 속도가 워낙 빠르면 짧은 시간 규모로 여러 프로그램들이  `CPU`를 번갈아서 실행하면 여러 프로그램이 동시에 실행되는 것 처럼 보인다.

`CPU`의 작업시간을 여러 프로그램들이 조금씩 나누어 쓰는 시스템을 `시분할 시스템`이라고 한다.

그리고, 여러 프로그램을 같이 실행하지만 사용자 관점에서는 입력의 결과를 즉시 받기 떄문에 `대화형 시스템`이라고도 불린다.


- **다중 프로그래밍 시스템**

메모리 공간을 분할해 여러 프로그램들을 동시에 메모리에 올려놓고 처리하는 시스템.

- **다중 처리기 시스템**

하나의 컴퓨터 안에 CPU가 여러개 설치되어 있는 경우를 뜻하므로 다른 개념들과 조금 다르다.

`CPU` 가 여럿 있는 컴퓨터는 서로 다른 `CPU`에서 프로그램이 동시에 실행 될 수 있어서 더욱 처리가 빨라지지만,

운영체제 입장에서는 관리를 해야하는 부분이 더 많아 진것이기 때문에 더욱 복잡한 메커니즘이 필요해진다.

---

#### 다중 사용자에 의한 동시 지원 여부에 따른 분류

- **단일 사용자용 운영체제**

한번에 한명의 사용자만이 사용하도록 허용하는 운영체제

- **다중 사용자용 운영체제**

여러 사용자가 동시에 접속해 사용할 수 있게 해주는 운영체제

여기서, `웹서버`나 `이메일서버` 같은 흔히 서버라고 부르는 컴퓨터가 여기에 속한다.


---

#### 작업을 처리하는 방식에 따른 분류

- **일괄 처리 방식(batch Processing)**

**요청된 작업을 일정량씩 모아서 한꺼번에 처리하는 방식**이다.

처리해야하는 여러 작업들을 모아서 일정량이 쌓이면 일괄적으로 처리하고, 모든작업이 완전히 종료된 후에 결과를 얻을 수 있다.

그에따라, 사용자 입장에서 응답시간이 길다는 단점이 존재한다.


- **시분할 방식**

여러 작업을 수행할 때 컴퓨터의 처리 능력을 일정한 시간 단위로 분할해 사용하는 방식.

사용자의 요청에 대한 결과를 곧바로 받을 수 있어서 대화형 시스템이라고도 표현한다.


- **실시간 운영체제**

**정해진 시간 안에 어떠한 일이 반드시 처리됨을 보장하는 시스템**에서 사용된다.

다시 말해 일정시간 안에 작업을 완료하지 못하면 동작 자체가 안되거나 큰 위험을 초래할 가능성이 있는 시스템에서 사용된다.

실시간 시스템은 시간제약의 중요성에 따라서 `경성 실시간 시스템` 과 `연성 실시간 시스템` 으로 나뉜다.

1) `경성 실시간 시스템` - 주어진 시간을 지키지 못할 경우 매우 위험한 결과를 초래할 가능성이 있는 시스템 ( 로켓, 원자로 제어시스템 )
2) `연성 실시간 시스템` - 데이터가 정해진 시간 단위로 전달되어야 올바른 기능을 수행할 수 있는 시스템 ( 멀티미디어 스트리밍 시스템 )

`연성 실시간 시스템`은 시간이 지켜지지 않을 경우 동영상 재생이 끊기거나 그 내용이 전달이 정확히 안될 수는 있지만

`경성 실시간 시스템`처럼 위험한 결과를 초래하지는 않는다.




## 출처

### [운영체제와 정보기술의 원리](http://www.yes24.com/Product/Goods/90124877)

