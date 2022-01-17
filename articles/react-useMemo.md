## react-useMemo

이 리포지토리는 react-useMemo에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### UseMemo 란?
useMemo는 렌더링 최적화를 위해 사용되는 hook 으로써 [**메모이제이션**](#메모제이션이란)된 값을 반환합니다.
생성(create) 함수와 의존성 값의 배열을 전달합니다. useMemo는 의존성이 변경되었을 때에만 메모이제이션된 값만 다시 계산 합니다. 이 최적화는 모든 렌더링 시의 고비용 계산을 방지하게 해 줍니다.
useMemo로 전달된 함수는 렌더링 중에 실행하며 배열이 없는 경우 매 렌더링 때마다 새 값을 계산하게 됩니다.

<br />

### UseMemo 사용이유
React 에서 Component는 상태(State) 의 값이 변경 될 때마다 렌더링이 됩니다.
하지만 값이 변경 되지 않았는데 값을 재설정 하는 것은 불필요합니다.
여러가지 연산을 통해 값을 사용해야 하는 경우 값이 변경되지 않았는데 굳이 매번 많은 연산을 통해 값을 재 할당할 필요가 없습니다.
useMemo 를 사용하여 이를 해결할 수 있습니다.
 
<br />
 
### UseMemo UseCallback 차이점
useMemo는 메모이제이션 된 값을 반환하고 useCallback은 메모이제이션 된 콜백을 반환합니다. 여기서 콜백을 반환 한다는 것은 콜백 함수를 메모리에 올려놓고 사용한다는 의미입니다.

<br />
 
#### 메모제이션이란?
메모이제이션(memoization)은 컴퓨터 프로그램이 동일한 계산을 반복해야 할 때, 이전에 계산한 값을 메모리에 저장함으로써 동일한 계산의 반복 수행을 제거하여 프로그램 실행 속도를 빠르게 하는 기술이다.


