## react-memo

이 리포지토리는 react-memo에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### React.Memo 란?
React.memo는 고차 컴포넌트(Higher Order Component)입니다.
컴포넌트가 동일한 props로 동일한 결과를 렌더링해낸다면, React.memo를 호출하고 결과를 메모이징(Memoizing)하도록 래핑하여 경우에 따라 성능 향상을 누릴 수 있습니다. 즉, React는 컴포넌트를 렌더링하지 않고 마지막으로 렌더링된 결과를 재사용합니다.

<br />

### React.Memo 와 React.useMemo 공통점
React.memo와 useMemo 모두 이전 props와 동일하면 인자로 넘긴 함수는 재실행되지 않고, 이전의 메모이즈된 결과를 반환한다는 점에서 동일하게 동작합니다.

<br />

### React.Memo 와 React.useMemo 차이점
useMemo는 hook이고 React.memo()는 HOC으로 다른 종류입니다.

<br />

### React.Memo 사용


<br />
