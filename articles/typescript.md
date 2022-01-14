## TypeScript
  
이 리포지토리는 TypeScript 기술을 활용하는데 필요한 설명을 다루는 Article입니다.
이 리포지토리는 DevNcore팀이 관리하고 있습니다.  

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
  
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/wpf-code-rules/stargazers"><img src="https://img.shields.io/github/stars/devncore/wpf-code-rules" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/wpf-code-rules" alt="License"> | <a href="https://github.com/devncore/wpf-code-rules/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/wpf-code-rules" alt="Commits-per-month"></a> |

## 내용
- [아키텍쳐](#아키텍쳐)
- [Type](#type)

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
