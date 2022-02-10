## react-useRef

이 리포지토리는 react-useRef에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### useRef 란
`useRef`란 특정 DOM(태그, 컴포넌트)을 선택할 수 있게끔 해주는 Hooks의 한 종류입니다.    
작업을 하다보면 html tag, 커스텀 컴포넌트 객체를 가져와야 할 일이 생깁니다. 가령 특정 엘리먼트 크기를 가져와야 한다던지 스크롤바 위치를 가져오거나 설정해야 한다던지.. (JavaSript에선 getElementById함수로 DOM 정보를 가져올 수 있습니다.) 그럴 때 `useRef` 라는 Hook을 사용합니다.

### useRef vs getElementById
일반적으로 리액트에서 개발할 땐 useRef가 document.getElementById보다 좋다고 합니다.    
왜냐하면 리액트로 된 나머지 코드들과 더 잘 맞고 컴포넌트는 여러 개의 인스턴스를 가질 수 있기 때문에 엘리먼트의 id를 사용하면 id가 중복될 수 있기 때문입니다.

### useRef 테스트 코드
```JSX
import React, {useRef} from "react";

export default function UseRefTest() {

const handleClick = () => {
    //Id입력 input이 null or WhiteSpace일 때 Id입력 Input에 커서 이동
    if(!domId.current.value) {
        alert("Id를 입력해주세요.")
        domId.current.focus();
        return;
    }
    //Password입력 input이 null or WhiteSpace일 때 Password입력 Input에 커서 이동
    if(!domPassword.current.value) {
        alert("비밀번호를 입력해주세요.")
        domPassword.current.focus();
        return;
    }

    alert("모두 입력");
}

    const domId = useRef(null);
    const domPassword = useRef(null);
    return (
        <div style={{margin: "50px auto 0 auto", display: "flex", flexDirection: "column" }}>
            <input type="text" ref={domId} style={{}}/>
            <input type="password" ref={domPassword} style={{marginTop: "10px", marginBlock: "10px"}}/>
            <button onClick={handleClick}>클릭</button>
        </div>
    );
}
```
