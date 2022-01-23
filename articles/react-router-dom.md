## React Router Dom

이 리포지토리는 React Router Dom에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

## 내용
- [React Router Dom 이란?](#react-router-dom-이란)
- [페이지 이동 (History](#페이지-이동-history)
- [화면 스위칭 (Route)](#화면-스위칭-route)
- [파라미터 넘겨받기 (Match)](#파라미터-넘겨받기-match)
- [Effect Hook 활용](#effect-hook-활용)
- [버전 이슈](#버전-이슈)

## React Router Dom 이란?
- 페이지의 로딩 없이 페이지에 필요한 컴포넌트를 불러와 렌더링하여 보여주는 것
- React는 SPA 방식이기 때문에 해당 요청에 맞는 컴포넌트만 라우팅하여 부분적으로 렌더링해야 함

## 페이지 이동 (History)
React는 하나의 단일 페이지(Single Page Application)를 구성하기 때문에 페이지 이동 시 기존 웹 방식의 `localhost.href`를 사용하는 것은 썩 좋은 방법은 아닙니다.
 
#### 기존 방식 살펴보기
```jsx
window.location.href = "/users";
```
기존 정적(Static) 방식으로 페이지를 이동시킬 경우 불필요한 Refresh가 일어나며 React는 내부적으로 앱을 새로 시작하게 됩니다.
> React는 SPA 방식인 관계로 새로고침(F5)이 일어나는 순간 모든 것을 새롭게 시작합니다.

#### React 방식 살펴보기
> 실제 정적 페이지를 찾는 것이 아닙니다.
```jsx
history.push("/users");
```
이 코드는 앞서 살펴본 `location.href` 방식과 동일한 기능(새로고침)처럼 동작하지만 실제로는 새로고침이 일어나지 않습니다. 
**Route 컴포넌트**를 통해 해당 영역이 스위칭되어 마치 화면이 이동된 것처럼 보이게 됩니다. 

___그렇다면 Router를 통한 화면 스위칭을 어떻게 해야 할까요?___

Route 컴포넌트를 통해 손쉽게 경로 규칙을 만들 수 있습니다.

## 화면 스위칭 (Route)
Route 컴포넌트는 `react-router` 라이브러리에 포함되어 있습니다.

```jsx
import { Route } from "react-router";
```

___이제 Route를 통해 화면 스위칭을 구성해볼까요?___

index.js를 통해 DOM 객체가 로드(Render) 되는 메인 중심 페이지에서 Route 규칙을 만들도록 합니다.

#### Route 주요 속성들
| 속성 | 설명 |
|:----|:----|
| path | 컴포넌트와 매칭되는 `url`을 정의합니다. |
| component |`url`과 `path`가 일치할 경우 보여지는 컴포넌트를 정의합니다. |

#### Route 규칙 만들기
```jsx
<Switch>
    <Route path="/users" component={<Users/>}/>
    <Route path="/orders" component={<Orders/>}/>
</Switch>
```
사실 Route를 반드시 Switch로 묶어야 하는 것은 아니지만, 일반적으로 Switch를 사용하는 것이 편리합니다.

Switch를 사용하지 않는 대신 exact 속성을 통해서도 각각의 url과 컴포넌트 화면을 매칭시킬 수 있습니다. 

이제 마지막으로 라우터를 허용하는 영역을 **BrowserRouter**를 통해 감싸주어야 합니다. 

이 영역의 범위를 선택하는 기준은 다양하지만 보통 index.js 파일에서 메인 컴포넌트 전체를 감싸도록 하는 것이 일반적입니다.

#### BrowserRouter 추가하기
```jsx
ReactDOM.render(
    <BrowserRouter>
        <Portal/>
    </BrowserRouter>,
    document.getElementById("root");
);
```
하지만 BrowserRouter는 Route를 감싸줄수만 있다면 어느 위치에 존재해도 상관은 없습니다.

## 파라미터 넘겨받기 (match)
자식 컴포넌트의 생사(생명주기)는 이제부터 Router의 스위칭 역할에 달렸습니다.

Route의 매칭 여부에 의해 해당 컴포넌트가 보여지게 됩니다. 그리고 브라우저를 통해 전달받은 `url` 값을 사용할 수도 있습니다.

#### 파라미터(Parameter) 정의
화면 `URL`과 함께 파라미터 변수를 전달받기 위해 Route에서 기존 path에 `/:id`를 추가합니다.
```jsx
<Route path="/users/:id" component={<Users/>}/>
``` 
___앞으로는 users와 함께 :id 값을 보내야 합니다.___

올바른 URL은 앞으로 이렇게 될 것입니다.
> https://example.com/users/2022

___리엑트에서는 어떻게 이동할까요?___

useHistory를 사용합니다.

```jsx
const userId = "";
history.push(`/users/${userId`);
```
크게 다른 점은 없지만 `/users/` path에 이어서 `id` 파라미터 값을 추가했습니다.

#### 컴포넌트에서 파라미터 받기
이제 `URL`이 변경될때마다 함께 포함된 파라미터 값을 전달받는 방법을 확인해보겠습니다.

#### 파라미터(Parameter) 추출
```jsx
const Users = (props) => {
    const { id } = props.match.params;
    return (
        <div>id: {id}</div>
    );
}

export default Users;
```

## Effect Hook 활용
```jsx
React.useEffect(() => {
    // something!!
}, [id]);
```

## 버전 이슈
#### useHistory(5.3.0) > useNavigate(6.2.1)
react-router-dom 6.2.1 버전에선 useHistory가 useNavigate로 변경 되었습니다.

- 5.3.0(기존)
```jsx
import { useHistory } from "react-router-dom";
const history = useHistory();
history.push(`/users/${userId`); 
```

- 6.2.1(변경)
```jsx
import { useNavigate } from "react-router-dom";
const navigate = useNavigate();
navigate(`/users/${userId`); 
```
