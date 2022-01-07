## 로컬 프록시 연결 설정



### 프록시 연결목적

기존 프로젝트는 API와 클라이언트가 합쳐져 있는 경우가 많지만
이제는 API와 클라이언트를 분리시켜 개발을 진행하는 방식이 많아지는 추세이다.
분리가 될 경우 개발정보와 배포된정보로 분기되며 정보에 맞게 URL을 변경을 해야한다.

<br />

### 프록시 연결 방법

> 로컬개발 설정정보

```
PORT=3000
REACT_APP_SERVICE_URL='https://localhost:5451'
```

> 배포파일 설정정보

```
REACT_APP_SERVICE_URL='https://.example.com'
```

```
REACT_APP_SERVICE_URL=''
```

> 실제로 URL 변경해주는방식

```
export const find = (name) => {
    return process.env.REACT_APP_SERVICE_URL + name;
}
```


