## Axios

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
}
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
