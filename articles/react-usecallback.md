## react-usecallback

이 리포지토리는 react-usecallback에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### useCallback 이란?
useCallback 은 특정 함수를 새로 만들지 않고 재사용하고 싶을때 사용합니다.
useCallback은 콜백의 메모이제이션된 버전을 반환하며 메모이제이션된 버전은 콜백의 의존성이 변경되었을 때에만 변경됩니다. 이것은, 불필요한 렌더링을 방지하기 위해 참조의 동일성에 의존적인 최적화된 자식 컴포넌트에 콜백을 전달할 때 유용합니다.

<br />

### useCallback 기본

```jsx
const memoizedCallback = useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b],
);
```


#### useCallback 사용예시
```jsx
export default function Exam(props) {
    const [text, setText] = React.useState("");
    const [name, setName] = React.useState("react");
    const getName = useCallback(() => {
        return "Name is " + name;
    }, [name]);
    
    React.useEffect(() => {
        setText(getName());        
    }, [getName]);

    return (
        <>useEffect. {text}</>
    );
}
```

**Effect** 안에서 사용되는 함수를 `useCallback`으로 한번 감싸고 콜백 함수의 의존 속성 `[name]` 을 지정합니다. 그리고 Effect에서는 함수의 변경 여부를 `[getName]` 으로 판단하여 **의존 속성값이 변경되었을때만 호출(Callback)** 할 수 있습니다.

```jsx
export default function Nodes(props) {
    const [query, setQuery] = React.useState("React");

    const fatchData = useCallback(() => {
        const url = "https://localhost:7073/api/menus/" + query;
    }, [query]);

    function Item( {fetchData}) {
        let [data, setData] = React.useState(null);
        useEffect(() => {
            fetchData().then(setData);
        }, [fetchData]);
    }
    return <Item fetchData={fetchData}/>
}
```

#### UseRef
```jsx
const [count, setCount] = React.useState(0);
const latestCount = useRef(count);
// latestCount.current
```

* * *

#### useCallback 테스트 코드
- **useCallback 미적용**    

SmartHome.js
```JSX
import React, { useState, useCallback } from "react";


export default function SmartHome() {
  const [bedOn, setBedOn] = useState(false);
  const [kitchenOn, setKitchenOn] = useState(false);
  const [bathOn, setBathOn] = useState(false);

  const toggleBed = () => setBedOn(!BedOn);
  const toggleKitchen = () => setKitchenOn(!kitchenOn);
  const toggleBath = () => setBathOn(!bathOn);

  return (
    <div style={{display: "table", margin: "50px auto auto auto"}}>
      <Light room="침실" on={bedOn} toggle={toggleBed} />
      <Light room="주방" on={kitchenOn} toggle={toggleKitchen}/>
      <Light room="욕실" on={bathOn} toggle={toggleBath} />
    </div>
  );
}
```

Light.js
```JSX
import React from "react";

export default function Light({ room, on, toggle }) {
    console.log({ room, on });
    return (
      <button onClick={toggle}>
        {room} {on ? "💡" : "⬛"}
      </button>
    );
  }
```

침실조명만 on하고 콘솔을 확인해 보면 침실 Light 컴포넌트 조명만 변경 됐지만 주방, 욕실 Light 컴포넌트도 호출된 걸 확인할 수 있습니다.
```JSX
{room: "침실", on: true}
{room: "주방", on: false}
{room: "욕실", on: false}
```

- **useCallback 적용**    
SmartHome.js
```JSX
import React, { useState, useCallback } from "react";


export default function SmartHome() {
  const [bedOn, setBedOn] = useState(false);
  const [kitchenOn, setKitchenOn] = useState(false);
  const [bathOn, setBathOn] = useState(false);

  const toggleBed = useCallback(() => setBedOn(!bedOn), [bedOn]);
  const toggleKitchen = useCallback(() => setKitchenOn(!kitchenOn),[kitchenOn]);
  const toggleBath = useCallback(() => setBathOn(!bathOn), [bathOn]);

  return (
    <div style={{display: "table", margin: "50px auto auto auto"}}>
      <Light room="침실" on={bedOn} toggle={toggleBed} />
      <Light room="주방" on={kitchenOn} toggle={toggleKitchen}/>
      <Light room="욕실" on={bathOn} toggle={toggleBath} />
    </div>
  );
}
```

Light.js
```JSX
import React from "react";

export default function Light({ room, on, toggle }) {
    console.log({ room, on });
    return (
      <button onClick={toggle}>
        {room} {on ? "💡" : "⬛"}
      </button>
    );
  }
  
Light = React.memo(Light);
```
