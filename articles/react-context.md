## React Context

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

export const PortalContext = createContext({
    menu: "",
    menuChange: () => {}
});

function Portal(props) {
    const [menu, setMenu] = useState("");
    const menuChange = () => {
        //
    };
    return (
        <PortalContext.Provider value={{ menu, menuChange }}>
            {props.children}
        </PortalContext.Provider>  
    );
}

export default Portal;
```