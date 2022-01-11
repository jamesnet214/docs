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

**Effect** 안에서 사용되는 함수를 `useCallback`으로 한번 감싸고 함수의 의존성(name)을 등록하고, Effect에서는 함수의 변경 여부를 **판단하여 호출(Callback)** 할 수 있습니다.
