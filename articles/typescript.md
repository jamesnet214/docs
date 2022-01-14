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

## 타입스크립트란?
Microsoft에서 개발하여 2012년에 발표한 자바스크립트의 슈퍼셋인 오픈소스 프로그래밍 언어이며 JavaScript에 정적 타이핑과 ES2015를 기반으로 하는 객체지향적 문법이 추가된 것을 주요 특징으로 한다. 엄격한 문법을 지원하며 C#의 리드 아키텍트이자 델파이, 터보 파스칼의 창시자인 Anders Hejlsberg가 개발에 참여했다. 클라이언트 사이드와 서버 사이드를 위한 개발에 사용할 수 있으며 자바스크립트의 슈퍼셋이기 때문에 자바스크립트로 작성된 프로그램이 타입스크립트 프로그램으로도 동작한다. 타입스크립트에서는 자신이 원하는 타입을 정의하고 프로그래밍을 하면 자바스크립트로 컴파일되어 실행이 가능하다. 타입스크립트는 모든 운영 체제, 모든 브라우저, 모든 호스트에서 사용 가능한 오픈 소스이다.

## 타입스크립트를 쓰는이유
자바스크립트는 동적이며 자료형이라는 개념이 존재하지 않습니다.
속성의 변경이 쉽고 자유로운데 이로 인하여 변경이 잘못되었다는 것을 실행중에 확인이 가능합니다.
문제는 테스트 버전에서 발견하지 못한 버그를 서비스를 운영중에 발견할 수 있다는 의미이기도 합니다.
이 부분을 TypeScript를 통하여 코드 작성 단계에서 타입을 체크해 오류를 확인할 수 있고 미리 타입을 결정하기 때문에 실행 속도 또한 무척 빠릅니다.
다른이유로는 MS에서 만들었고 튜토리얼등이 매우 잘 되어 있으며 오픈소스화 등이 있습니다.

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
