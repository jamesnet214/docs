## Single Page Application (SPA)

이 리포지토리는 SPA에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### SPA 란?
`Single Page Application`의 약자로 페이지가 1개인 어플레케이션이란 뜻입니다.    
웹 실행에 필요한 모든 정적 리소스를 최초에 한번만 다운로드 후 새 페이지(html)를 불러오지 않고 현재 페이지를 동적으로 다시 작성합니다. 즉 하나의 페이지에 여러 페이지를 클라이언트에서 자바스크립트로 구현하는 방식입니다.

### SPA가 생겨난 배경
기존 웹사이트([**MPA**](#MPA-란))방식은 지금보다 전달되는 페이지(html)의 용량이 작았습니다. 그래서 새로운 페이지를 서버에서 전송([**Server Side Rendering**](#Server-Side-Rendering-이란)) 해 주었는데 점차 웹사이트가 고도화되며 페이지의 용량이 커져가 매번 새로운 페이지를 전달하는 것이 버거워지게 되어 SPA가 등장하게 되었습니다. 

### SPA 장단점
**장점**
1. 새 페이지를 렌더하여 새로 보내주는 방식이 아닌 변화가 일어난 요소만 다시 렌더하는 방식이기 때문에 깜빡 거림이 없고 속도가 빠르며 재사용성이 높습니다.
2. 서버 부담이 경감됩니다.
3. 컴포넌트 개발이 용이합니다.

**단점**
1. 초기 구동 속도가 느립니다.
2. 검색엔진 봇이 사이트를 돌아 다니며 사이트의 웹 문서 파일을 읽는데(주로 html 파일) SPA 방식은 페이지가 하나이며 필요한 부분을 자바스크립트로 바꿔주기 때문에 **검색엔진최적화**가 어렵습니다.   (포털 사이트 중 Google은 자바스크립트를 읽을 수 있다고 하지만 이 또한 봇 할당량이 높아져 비추천 한다고 하며 다른 검색엔진은 자바스크립트를 읽을 수 없다고 합니다.)
3. 


### SPA를 사용중인 사이트 목록
- [x] Facebook

<br />

#### MPA 란 
`Multiple Page Application`의 약자로 페이지가 여러개인 어플리케이션이란 뜻입니다.

#### Server Side Rendering 이란
서버에서 사용자에게 보여줄 페이지를 모두 구성하여 클라이언트에 보내 사용자에게 페이지를 보여주는 방식입니다.





