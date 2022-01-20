## React Router Dom

이 리포지토리는 React Router Dom에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

## React Router Dom 이란?
- 페이지의 로딩 없이 페이지에 필요한 컴포넌트를 불러와 렌더링하여 보여주는 것
- React는 SPA 방식이기 때문에 해당 요청에 맞는 컴포넌트만 라우팅하여 부분적으로 렌더링해야 함

## 페이지 이동 (History)
React는 하나의 단일 페이지(Single Page Application)를 구성하기 때문에 페이지 이동 시 기존 웹 방식의 `localhost.href`를 사용하는 것은 썩 좋은 방법은 아닙니다.
 
#### 기존 페이지 이동 방식
```
window.location.href = "/users";
```
기존 정적(Static) 방식으로 페이지를 이동시킬 경우 불필요한 Refresh가 일어나며 React는 내부적으로 앱을 새로 시작하게 됩니다.
> React는 SPA 방식인 관계로 새로고침(F5)이 일어나는 순간 모든 것을 새롭게 시작합니다.
