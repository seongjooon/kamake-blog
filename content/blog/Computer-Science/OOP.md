---
title: 'OOP(객체 지향 프로그래밍)'
date: 2019-8-23 18:10:03
category: 'Computer-Science'
---

> ## OOP (Object Oriented Programming)

- OOP란 무엇인가?
  객체를 위주로 코드를 정리하는 것이다. 객체가 기능을 담당하기도 한다. (추가하거나 제거하기도 한다.)

OOP is a programming paradigm organized around objects rather than actions and logic.
=> 쓰기 쉽고 편한 물건을 창조해서 만들어내는 것. 무에서 유를 창조한다는 것. 창의적인 사고에서 나온다. 따라서 재료가 될 가이드 정도는 있을 수 있겠지만 정답은 없으므로 프로그래머가 어떻게 만들어내는지가 중요하다.
(객체는 우리가 만들고자 하는 물건에 재한 관련 정보나 기능 또는 행동들을 가질 수 있다.)

Q. 그렇다면 창의력을 높이려면 어떻게 해야하는가?
어떤 이들은 "인생을 살아오는 동안 창의력은 거의 정해진다. 하지만 여러가지 방식으로 보고 느끼고 경험하고 배우면 가능해질 수 있다." 라고 말한다.

=> 창의력에 대한 나의 의견은 선천적으로 타고난 사람이 아니라면 아이디어가 없이는 창조해내기란 쉽지 않은 일이다. 그렇기 때문에 새롭고 좋은 아이디어를 고안해내야하는 상황에서는 그 분야에 대한 많은 양과 질의 아이디어를 수집하고 이해해야 결국엔 창의적인 아이디어가 나온다고 생각한다.

객체 지향이라는 개념은 명확한 정의가 없다. 그렇기 때문에 특성을 통해 이해해야한다. 실존하는 객체의 형태의 것을 추상화를 통해 소프트웨어상에서 구현하려는 패러다임이다. 쉽게 말하자면 사물을 인지하는 방식을 접목하는 사상이다.

```js
const speaker = {
  volume: 0,
  volumeUp: function() {
    this.volume += 20
  },
  volumeDown: function() {
    this.volume -= 20
  },
}

speaker.volumeUp() // volume: 20
speaker.volumeUp() // volume: 40
speaker.volumeDown() // volume: 20
speaker.volume = 0 // volume: 0
```

> ### Encapsulation (캡슐화)

캡슐화는 정보를 은닉(information hiding)하는 것과 비슷하다. 개발자가 사용자로부터 정보를 보호하거나 노출시키는 것이다. 객체의 속성을 외부에서 사용자가 접근할 수있는 상황일때, 내부 정보를 보호해야한다면 캡슐화로 보호해줄 수 있다.

```js
// IFFE로 Encapsulated
const speaker = function() {
  let volume = 0

  return {
    volumeUp: function() {
      this.volume += 20
    },
    volumeDown: function() {
      this.volume -= 20
    },
  }
}

speaker.volumeUp() // volume: 20
speaker.volumeUp() // volume: 40
speaker.volumeDown() // volume: 20
speaker.volume = 0 // But, // volume: 20
// => 캡슐화를 적용해서 외부에서 객체 내부의 변수를 보호할 수 있다.
```

> ### Abstraction (추상화)

현실 세계의 사물들을 객체라고 보고 그 객체로부터 개발하고자 하는 애플리케이션에 필요한 특징들을 뽑아와 프로그래밍 하는 것이다. 이것을 추상화라한다. 복잡한 원리나 구동방식을 굳이 사용자에게 상세하게 알려줄 필요가 없다.

ex) 셀룰러폰에는 일반적으로 자동잠금 기능이 있다. 사용자가 임의로 설정하는 것이 아니라면 자동잠금 장치로 인해 배터리사용량을 보호할 수 있다. 이때 사용자에게 자동잠금의 기능을 상세히 알려줄 필요가 없다.

### 생성자 함수로 Constructor를 활용할 수 있다.

(Class)컨스트럭터를 사용하면 **재사용** 할 수 있다.

```js
function Speaker() {
  this.volume = 0
}
Speaker.prototype.volumeUp = function() {
  this.volume += 20
}
Speaker.prototype.volumeDown = function() {
  this.volume -= 20
}
Speaker.prototype.autoOnAndOff = function() {
  const that = this
  setTimeout(function() {
    that.volume = 0
  }, 500)
}
const speaker1 = new Speaker()
const speaker2 = new Speaker()
const speaker3 = new Speaker()
```

> ### Factory function

함수가 객체를 리턴하게 만든다. => 객체를 리턴한 함수를 이용하는 것이다.
함수가 객체를 리턴하는데, 컨스트럭터나 클래스가 아닌 경우에는 팩토리 함수다.
new 키워드를 활용해서 쓴다면 조심해야한다. 수정한다면 대대적인 작업이 될 확률이 높다.

```js
const speakerPrototype = {
  volumeUp: function() {
    this.volume += 20
  },
  volumeDown: function() {
    this.volume -= 20
  },
  autoOnAndOff: function() {
    setTimeout(() => {
      that.volume = 0
    }, 500)
  },
}
// 리터럴 형식
function createSpeaker() {
  let volume = 0 // 외부에서 건들지 못하도록 보호

  return {
    volumeUp: function() {
      volume += 20
    },
    volumeDown: function() {
      volume -= 20
    },
    autoOnAndOff: function() {
      setTimeout(() => {
        volume = 0
      }, 500)
    },
  }
}

const speaker1 = createSpeaker()
const speaker2 = createSpeaker()
const speaker3 = createSpeaker()
```

```js
// Factory function
function createSpeaker() {
  //this
  return Object.create(speakerPrototype)
}

const speaker1 = createSpeaker()
const speaker2 = createSpeaker()
const speaker3 = createSpeaker()
```

> ### Inheritance

```js
function Macbook(name) {
  this.name = name
}
Macbook.prototype.turnOff = function() {
  power = 100
}

function Macmini(name) {
  Macbook.call(this, name) // 하위 클래스인 Macmini에서 상위클래스인 Macbook의 this 값을 임의로 지정해준다.
  this.power = 0
}
Macmini.prototype = Object.create(Macbook) // 에러의 기능을 고릴라에러에서 사용하기 위한 방법이다.
Macmini.prototype.constructor = Macmini /* 해당라인의 상단 라인을 실행하지 않는다면 Macmini의 컨스트럭터는 Macmini일것이다. 하지만 상단 라인을 실행함으로 인해 Macmini의 컨스트럭터는 Macbook가 된다. 기존의 참조 값을 유지 시켜주기위해서는 다시한번 더 할당해주어야 한다.*/
```

> ### 참고

- 외부로부터 정보를 보호하기 위해서 리터럴형식으로 팩토리함수를 구성할 것인지, 설명서를 제공하면서 주의를 주는 방향으로 컨스트럭터로 구성할 것인지 개발자가 선택하면 된다.

- OOP는 상황에 맞게 쓰이고 있는가? 쓸모있는 기능인가? 확인해야한다.

- **SOLID Principle(객체 지향 설계)**
  - SRP(Single Responsibility Principle) : 단일 책임 원칙
    클래스는 단 하나의 책임을 가져야 하며 클래스를 변경하는 이유는 단 하나의 이유이어야 한다.
  - OCP(Open-Closed Principle) : 개방-폐쇄 원칙
    확장에는 열려 있어야 하고 변경에는 닫혀 있어야 한다.
  - LSP(Liskov Substitution Principle) : 리스코프 치환 원칙
    상위 타입의 객체를 하위 타입의 객체로 치환해도 상위 타입을 사용하는 프로그램은 정상적으로 동작해야 한다.
  - ISP(Interface Segregation Principle) : 인터페이스 분리 원칙
    인터페이스는 그 인터페이스를 사용하는 클라이언트를 기준으로 분리해야 한다.
  - DIP(Dependency Inversion Principle) : 의존 역전 원칙
    고수준 모듈은 저수준 모듈의 구현에 의존해서는 안된다.

객체 지향 프로그래밍의 치명적인 단점은 함수형 프로그래밍 패러다임의 등장 배경을 통해서 알 수 있다. 바로 객체가 상태를 갖는다는 것이다. 변수가 존재하고 이 변수를 통해 객체가 예측할 수 없는 상태를 갖게 되어 애플리케이션 내부에서 버그를 발생시킨다는 것이다. 이러한 이유로 함수형 패러다임이 주목받고 있다.
