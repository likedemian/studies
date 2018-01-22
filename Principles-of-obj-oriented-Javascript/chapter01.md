# 원시 타입과 참조 타입

개발자 대부분은 자바나 C# 같은 클래스 기반 언어를 사용하면서 객체지향 프로그래밍을 배운다. 하지만 이런 개발자들은 자바슼릡트를 배울 떄 갈피를 잡지 못하는 경우가 많은데 자바스크립트에서는 처음부터 클래스를 정의하지 않고도 코드를 작성할 수 있으며 필요에 따라 데이터 구조를 만들어서 사용한다. 클래스가 없으므로 패키지와 같이 클래스를 그룹으로 묶는 기능도 없다. 자바 같은 언어에서는 패키지 이름과 클래스 이름을 통해 사용할 객체의 종류와 프로젝트의 파일 및 폴더 구조를 정하지만, 자바스크립트에서는 백지 상태에서 프로그래밍을 시작하며 파일이든 폴더든 여러분이 원하는 대로 구성할 수 있다. 다른 언어의 파일 구조를 흉내 내는 이도 있고 자바스크립트의 유연함을 한껏 활용해 완전히 새로운 구조를 만들어내는 이도 있다. 아무런 지식이 없는 사람에게는 이러한 선택의 자유가 도리어 지나치게 느껴질 수도 있다. 하지만 익숙해지고 나면 여러분의 취향을 아주 쉽게 반영할 수 있을 정도로 자바스크립트가 매우 유연한 언어임을 깨닫게 될 것이다.

자바스크립트는 전통적인 객체지향 언어를 배운 사람도 쉽게 배울 수 있도록 언어의 중심을 객체에 두고 있다. 자바스크립트에서 데이터 대부분은 객체이거나 객체를 통해 접근하는 값이다. 자바스크립트는 함수조차 객체로 표현하며 덕분에 자바스크립트의 함수는 *일급 함수(first-class functions)* 이다.

객체를 다루고 이해할 수 있어야 자바스크립트를 전체적으로 이해할 수 있따. 자바스크립트에서 객체는 언제든 만들 수 있고 객체의 프로퍼티(property) 또한 원한다면 언제든 추가하거나 제거할 수 있다. 자바슼르비트의 객체는 매우 유연하여 다른 언어에서는 쉽게 사용할 수 없었던 독특하고 흥미로운 패턴도 만들 수 있다.

이 장에서는 자바스크립트에 있는 두 종류의 타입, 즉 원시 타입과 참조 타입에 대해 알아보고 다룰 것이다. 두 타입 모두 객체를 통해 접근하지만 서로 다르게 동작하므로 차이점을 익혀두는 것이 좋다. 

## 타입이란?

자바스크립트에 클래스라는 개념은 없지만 이를 대체할 타입이라는 개념이 존재하며 타입은 크게 두 종류로 구분한다. 하나는 단순한 데이터를 저장하는 *원시 타입*이고 다른 하나는 객체로서 저장되는 *참조 타입*이다. 참조 타입은 사실 메모리상의 주소를 가리킨다.

자바스크립트에서는 일관성을 유지하기 위해 원시 타입도 참조 타입처럼 다룰 수 있도록 되어 있는데 이 떄문에 이해하기 어려워진 면이 있다.


다른 프로그래밍 언어는, 원시 타입은 스택에 저장하고 참조는 힙에 저장하여 원시 타입과 참조 타입을 구분하고 있지만 자바스크립트는 그렇지 안핟. 자바스크립트에서는 *변수 객체(variable object)*의 스코프를 따라 변수를 추적한다. 원시 타입의 원시 값은 바로 변수 객체에 저장되지만 참조 타입에서 변수 객체에 저장되는 참조 값은 메모리에 있는 실제 객체를 가리키는 포인터(pointer)이다. 원시 값과 참조 값은 일견 비슷해 보이지만 상당히 다르게 동작한다. 이에 대해서는 나중에 설명할 것이다.

원시 타입과 참조 타입에도 여러 종류가 있다.

## 원시 타입

원시 타입(primitive type)은 true와 25처럼 있는 그대로 저장되는 간단한 데이터를 표현한다. 자바스크립트에는 다섯 종류의 원시 타입이 있다.

* Boolean(불리언): true 또는 false
* Number(숫자): 정수 또는 부동소수점 실수 값
* String(문자열): 한 쌍의 작은 따옴표 또는 큰 따옴표로 감싼 일련의 문자 (자바스크립트에는 문자 타입이 따로 없다.)
* Null : null이라는 값만 있는 원시 타입
* Undefined: undefined라는 값만 있는 타입 (undefined는 아무런 값도 할당되지 않은 변수에 할당되는 값이다.)

앞의 세 종류(불리언, 숫자, 문자열)는 빗스한 방식으로 동작하지만 뒤의 두 종류(null과 undefined)는 조금 다르게 동작한다. 그에 대해서는 이 장 전반에 걸쳐 다루도록 하겠다. 모든 원시 타입에는 값을 표현하는 리터럴(literal) 형식이 있다. 리터럴(literal)이란 코드에 직접 입력된 이름이나 가격처럼 변수에 저장되지 않은 값을 의미한다. 다음은 리터럴 형식을 사용한 각 타입의 예제이다. 

```javascript
// 문자열
var name = "Nicholas";
var selection = "a";

// 숫자
var count = 25;
var cost = 1.51;

//불리언
var found = true;

// null
var object = null;

// undefined
var flag = undefined;
var ref; // 자동으로 undefined가 할당된다.
```

다른 많은 언어와 마찬가지로 자바스크립트 변수에는 원시 타입의 값이 바로 저장된다(객체의 포인터가 아니다). 원시 값을 변수에 할당하면 값이 변수로 복사된다. 다시 말해 등호 기호를 사용해 어떤 변수를 다른 변수에 할당하면 두 변수 모두 자신만의 데이터를 가지게 된다는 뜻이다. 다음 예를 보자.

```javascript
var color1 = "red";
var color2 = color1;
```

이 코드에서 color1에는 "red"라는 값이 할당되었고 color2에는 color1의 값을 할당했다. 따라서 color2에는 "red"가 저장되었다. color1과 color2는 같은 값을 가지고 있지만 두 값은 완전히 별개의 ㄱ밧이며 color2에 아무런 영향을 주지 않고 color1의 값을 바꿀 수 있다. 물론 color2를 바꿀 때도 마찬가지로 color1에 아무런 영향을 주지 않는다. 이는 두 값이 각 값당 하나씩 할당된 서로 다른 영역에 저장되어 있기 때문이다.

원시 값을 가지고 있는 각 변수는 독립된 저장 공간을 사용하기 때문에 다른 변수의 값을 바꿔도 영향을 받지 않는다. 다음 예를 보자.

```javascript
var color1 = "red";
var color2 = color1;

console.log(color1); // "red"
console.log(color2); // "red"

color1 = "blue";

console.log(color1); // "blue"
console.log(color2); // "red"
```

이 코드에서 color1의 값은 "blue"로 바뀌었지만 color2는 여전히 원래대로 "red"를 유지한다.


### 원시 타입 종류 확인

원시 타입의 종류는 typeof 연산자를 사용해 확인할 수 있다. typeof 연산자를 변수에 사용하면 변수에 저장된 데이터의 타입을 문자열로 반환한다. typeof 연산자는 문자열, 숫자, 불리언, undefined와 잘 동작한다. 다음은 typeof 연산자를 여러 종류의 원시 값에 사용할 때 볼 수 있는 출력 결과이다.


```javascript
console.log(typeof "Nicholas"); // "string"
console.log(typeof 10);         // "number"
console.log(typeof 5.1);        // "number"
console.log(typeof true);       // "boolean"
console.log(typeof undefined);  // "undefined"
```

예상했듯이 문자열 값에 typeof 연산자를 사용하면 "string"을 반환하고 숫자 값에 사용하면 "number"를 반환한다. 이때, 숫자가 정수인지 실수인지는 상관없다. 불리언일 때는 "boolean"을 반환하고, 값이 undefined일 때는 "undefined"를 반환한다.

다만 null은 조금 까다롭다. 

다음 코드의 실행 결과를 처음 본 개발자라면 이해하기 어려운 것이 당연하다.

```javascript
console.log(typeof null); // "object"
```

typeof null을 실행하면 결과는 "object"이다. 그런데 null이 객체라는 까닭은 무엇일까? (사실 이는 자바스크립트 언어를 설계하고 관리하는 TC39 위원회에서 실수라고 인정했떤 부분이다. 덕분에 객체를 반환해야 할 때 null을 빈 객체 포인터처럼 생각할 수있지만 헷갈리는 것은 여전한다.)

이 같은 특성 때문에 null인지 아닌지를 확인할 때는 다음과 같이 null과 직접 비교하는 것이 가장 좋다.

```javascript
console.log(value === null); // true or false
```
