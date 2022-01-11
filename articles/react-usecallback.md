## react-usecallback

#### 기본적인 useCallback
```
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
