## React Context

이 리포지토리는 React Context에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

#### Context란?
**Context**는 하위 자식 컴포넌트에서 상위 부모 컴포넌트의 props를 다이렉트로 접근하기 위한 기술입니다.

일반적으로 자식 컴포넌트가 상위 부모 컴포넌트로 부터 props를 넘겨받는다면 별 문제가 없겠지만 상위 부무 컴포넌트가 많아 여러 레벨을 거치면서 props를 전달 받아야 한다면 생각보다 불편하고 불필요한 작업으로 느껴질 것입니다.

## Context 함수
Context 함수는 아래 두개만 사용하면 됩니다.

| - | Function | Info |
|:--:|:---|:----------| 
| 1 | createContext | Context 생성에 필요 |
| 2 | useContext | Context 사용에 필요 |

## Create Context
Context를 만들기 위해 **createContext**를 사용합니다.

```
import { createContext, useState } from 'react'
import Children from './Children';

export const PortalContext = createContext({
    menu: "",
    menuChange: () => {}
});

function Portal(props) {
    const [menu, setMenu] = useState("테스트");
    const menuChange = () => {
        //
    };
    return (
        <PortalContext.Provider value={{ menu, menuChange }}>
            <Children/>
        </PortalContext.Provider>  
    );
}

export default Portal;
```

## Use Context
하위 자식 컴포넌트에서 **useContext**를 사용합니다.

```
import { useContext } from 'react'
import { PortalContext } from './Portal';

function Children(props) {
    const portal = useContext(PortalContext)
   
    return (
          //'테스트' 출력
          <div>{portal.menu}</div>
          //'부모 menuChange 메서드 호출'
          <button onClick={portal.menuChange}>테스트 버튼</button>
    );
}
```
