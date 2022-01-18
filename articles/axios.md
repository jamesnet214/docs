## Axios for React

이 리포지토리는 React axios를 통한 API 호출방법을 소개합니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

#### React REST API 사용 방법
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
파라메터가 없는 기본 GET 방식의 API를 호출하는 기본 구문입니다.
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

1. GET
2. POST
3. DELETE
4. PUT
