## TypeScript
  
이 리포지토리는 TypeScript 기술을 활용하는데 필요한 설명을 다루는 Article입니다. <br />
이 리포지토리는 DevNcore팀이 관리하고 있습니다.  

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
  
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/wpf-code-rules/stargazers"><img src="https://img.shields.io/github/stars/devncore/wpf-code-rules" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/wpf-code-rules" alt="License"> | <a href="https://github.com/devncore/wpf-code-rules/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/wpf-code-rules" alt="Commits-per-month"></a> |

<br />

## 내용
- [TypeScript란?](#타입스크립트란)
- [타입스크립트를 쓰는이유](#타입스크립트를-쓰는이유)
- [아키텍쳐](#아키텍쳐)
- [Type](#type)
- [Interface](#Interface)
- [Type Alias](#Type-Alias)
- [Generics](#Generics)
- [기본문법](#기본문법)

<br />

## 타입스크립트란?
Microsoft에서 개발하여 2012년에 발표한 자바스크립트의 슈퍼셋인 오픈소스 프로그래밍 언어이며 JavaScript에 정적 타이핑과 ES2015를 기반으로 하는 객체지향적 문법이 추가된 것을 주요 특징으로 한다. 엄격한 문법을 지원하며 C#의 리드 아키텍트이자 델파이, 터보 파스칼의 창시자인 Anders Hejlsberg가 개발에 참여했다. 클라이언트 사이드와 서버 사이드를 위한 개발에 사용할 수 있으며 자바스크립트의 슈퍼셋이기 때문에 자바스크립트로 작성된 프로그램이 타입스크립트 프로그램으로도 동작한다. 타입스크립트에서는 자신이 원하는 타입을 정의하고 프로그래밍을 하면 자바스크립트로 컴파일되어 실행이 가능하다. 타입스크립트는 모든 운영 체제, 모든 브라우저, 모든 호스트에서 사용 가능한 오픈 소스이다.

<br />

## 타입스크립트를 쓰는이유
자바스크립트는 동적이며 자료형이라는 개념이 존재하지 않습니다.
속성의 변경이 쉽고 자유로운데 이로 인하여 변경이 잘못되었다는 것을 실행중에 확인이 가능합니다.
문제는 테스트 버전에서 발견하지 못한 버그를 서비스를 운영중에 발견할 수 있다는 의미이기도 합니다.
이 부분을 TypeScript를 통하여 코드 작성 단계에서 타입을 체크해 오류를 확인할 수 있고 미리 타입을 결정하기 때문에 실행 속도 또한 무척 빠릅니다.
다른이유로는 MS에서 만들었고 튜토리얼등이 매우 잘 되어 있으며 오픈소스화 등이 있습니다.

<br />

## 아키텍쳐
TypeScript는 ES5, ES6 자바스크립트 표준을 포함하는 상위 스크립트입니다.

| ES5 | ES6 | TypeScript |
|:----:|:----:|:----:|
| ECMAScript5 | ECMAScript6 | Microsoft TypeScript |

## Type
TypeScript는 기존 JavaScript와 달리 Type을 사용할 수 있습니다.

#### 변수선언 with 타입

```
let name = "Son";
let name: string = "Son";
```
이와 같이 타입을 지정할 경우 잘못된 값을 할당하면 에러를 반환합니다.
```
// TypeScript에서는 에러!
let name: string = 4936;
```

## Interface
인터페이스는 일반적으로 타입 체크를 위해 사용되며 typealias와 유사한 기능을 하며 여러가지 타입을 갖는 프로퍼티로 이루어진 새로운 타입을 정의합니다.
export를 사용하여 외부 파일에서도 사용할 수 있다.

```typescript
export interface Person {
	name: string;
  	age: number;
  	address: string;
}
```

## Type Alias
인터페이스와 비슷한 동작을 하지만 default값을 지정할 수 있다는 점이 다르며 Type Alias는 extends 나 implements가 될 수 없기에 상속을 통해 확장이 필요하다면 Type Alias 보다 인터페이스가 유리합니다.

```typescript
type Person {
	name: string;
  	age: number;
  	address: string;
}
```

## Generics
Generics은 타입스크립트에서 함수, 클래스, interface, type을 정의하는 시점에 매개변수나 반환값의 타입을 선언하기 어려운 경우 사용 합니다.
< T > 는 컨벤션이며 제네릭에 해당하는 타입에는 어떤 타입이라도 들어올 수 있으며 Myparams는 인수 타입에 의해(number) 타입 매개변수가 결정됩니다.

``` typescript
function MyParams<T>(param: T) {
	return {param}
}

const params = MyParams(10);
```

## 기본문법

TBD ...

기본 타입
타입스크립트는 다양한 기본 타입을 제공합니다.

변수에 타입 설정
함수에 타입 설정
Tuple: 배열의 타입 순서와 배열 길이를 지정할 수 있는 타입입니다.
Enum: Number 또는 String 값 집합에 고정된 이름을 부여할 수 있는 타입입니다. 값의 종류가 일정한 범위로 정해져 있는 경우에 유용합니다. 기본적으로 0부터 시작하며 값은 1씩 증가합니다.
Any: 모든 데이터 타입을 허용합니다.
Void: 변수에는 undefined와 null만 할당하고 함수에는 리턴 값을 설정할 수 없는 타입입니다.
Never: 특정 값이 절대 발생할 수 없을 때 사용합니다.


인터페이스
인터페이스는 타입을 정의한 규칙을 의미합니다.

변수와 함수에 활용한 인터페이스
인덱싱
딕셔너리 패턴
인터페이스 확장


오퍼레이터
Union 타입: 자바스크립트의 OR 연산자와 같은 의미의 타입입니다. Union 타입으로 지정하면 각 타입의 공통된(보장된) 속성에만 접근 가능합니다.
Intersection 타입: 자바스크립트의 AND 연산자와 같은 의미의 타입입니다. 각각의 모든 타입이 포함된 객체를 넘기지 않으면 에러가 발생합니다.


제네릭
한 가지 타입보다 여러 가지 타입에서 동작하는 컴포넌트를 생성하는데 사용됩니다. 제네릭이란 타입을 마치 함수의 파라미터처럼 사용하는 것을 의미합니다.

타입 추론
타입 추론이란 타입스크립트가 코드를 해석하는 과정을 뜻합니다.
가장 적절한 타입(Best Common Type): 배열에 담긴 값들을 추론하여 Union타입으로 묶어 나가는 것을 말합니다.
인터페이스와 제네릭을 이용한 타입 추론 방식


타입 단언
타입 단언이란 타입스크립트가 해석하는 것보다 더 확실한 목적을 가지고 개발자가 해당 코드에 타입을 직접 지정하는 것을 의미합니다.

타입 호환
타입 호환이란 특정 타입이 다른 타입에 잘 호환되는지를 의미합니다.
구조적 타이핑: 코드 구조 관점에서 타입이 서로 호환되는지를 판단하는 것입니다. 구조적으로 더 큰 타입은 작은 타입을 호환할 수 없습니다.


