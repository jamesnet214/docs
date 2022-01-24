## Axios For React

이 리포지토리는 React axios를 통한 API 호출방법을 소개합니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### Axios 란?
Axios는 브라우저, Node.js를 위해서 만들어진 Promise API를 활요하는 HTTP 비동기 통신 라이브러리 입니다.

<br />

### Axios 특징
- Axios는 운영환경에 따라서 브라우저간 XMLHttpRequest 객체 또는 Node.js의 HTTP API를 사용한다.
- Promise(ES6) API를 사용
- 요청(Request) 응답 (reply)을 JSON 형태로 자동 변경

<br />

### Axios 설치정보

```javascript
npm install axios
```

<br />

### Axios HTTP Methods

| 메소드 |     설명    | 기본사용코드 |
|:------:|:----------:|:------------:| 
| GET    | 데이터 조회 | axios.get(url,[,config])        |
| POST   | 데이터 생성 | axios.post(url, data[, config]) |
| PUT    | 데이터 수정 | axios.put(url, data[, config])  |
| DELETE | 데이터 삭제 | axios.delete(url[, config])     |

<br />

### Axios 응답제어

- .then <br />
비동기 통신이 성공했을 경우 .then() 콜백을 인자로 받아 결과값 처리가 가능합니다.

```javascript
.then(response) => {
        const res = response.data;
        console.log("res:", res);
    }
```

- .catch <br />
catch() 를 통해 오류를 처리합니다. error 객체에서는 오류에 대한 주요 정보를 확인할 수 있습니다.

```javascript
.catch(error => {
         console.log("err:", error); 
        });
    }
```

<br />

### React REST API 사용 방법
| Fatch | Axios | Ajax |
|:-----:|:------:|:----:|
| Image | Image | Image |
| -     | Data 속성을 사용하며 내부적으로 Data를 Json으로 자동 변환합니다. | - |

## 응답 스키마
axios는 아래처럼 응답 스키마를 json 형식으로 반환합니다.
```
{
    data: {},
    status: 200,
    statusText: "OK",
    headers: {},
    config: {},
    request: {}
}
```

## 동기식 처리
Axios는 동기식 메서드를 체인 메서드 방식으로 제공합니다.

#### GET 방식 (Standard)
- 파라미터가 없는 기본 GET 방식의 API를 호출하는 구문입니다.
```jsx
const url = "/api/users";
axios.get(url)
    .then(response) => {
        const res = response.data;
        console.log("res:", res);    
    })
    .catch((error) => {
        console.log("err", error);
    });
```

- 파라미터가 있는 GET 방식의 API를 호출하는 구문입니다.
```jsx
const url = "/api/users";
const data = {
    a = "a",
    b = "b",
    c = 1
}
axios.get(url, {params: data})
    .then(response) => {
        const res = response.data;
        console.log("res:", res);    
    })
    .catch((error) => {
        console.log("err", error);
    });
```

## 비동기식 처리

```jsx
async function fetchData(text, url, count) {
    await axios.get(url + "?count=" + count)
        .then(res => {
            const d = res.data;
            setUsers(d);
            console.log(":" + text, d);
        })
        .catch(error => {
            console.log("err:", error); 
        });
}

React.useEffect(async () => {
    console.log("start!");
    fetchData("first", "/api/test1", 10000);
    fetchData("second", "/api/test2", 500);
    console.log("end!");
});
```

```jsx
async function getUserInfo() {
    const result = null;
    try {
        await axios.get(url)
            .then(response) => {
            result = response.data;
        })
        .catch((error) => {
            console.log("Service error: ", error);
        });    
    } catch (error) {
        console.log("Function error: ", error);
    } finally {
        return result;
    }   
}

const init = (async () => {
    await getUserInfo();
});

init();
```

