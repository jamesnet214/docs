## Axios for React

이 리포지토리는 React axios를 통한 API 호출방법을 소개합니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

## 동기식 처리
Axios는 동기식 메서드를 체인 메서드 방식으로 제공합니다.
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

Async (await)
```
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
