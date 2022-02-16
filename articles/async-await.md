## async-await

이 리포지토리는 react-useMemo에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### async/await 이란?
async와 await는 자바스크립트의 비동기 처리 패턴 중 최근에 나온 문법입니다.

<br />

먼저 비동기 사용 이유에 대해서 알아봅시다.
```JSX
function laundry()
{
    console.log("빨래 시작");

    for (var i = 0; i <= 100; i+=20)
    {
        console.log(`빨래 ${i}% 완료`)
    }
}

function dishes()
{
    console.log("설거지 시작");

    for (var i = 0; i <= 100; i+=20)
    {
        console.log(`설거지 ${i}% 완료`)
    }
}

function start()
{
    laundry();
    dishes();
}

start();
```

<br />
<img src="https://user-images.githubusercontent.com/68521148/153867801-9ac9b573-4ec6-4c2d-bb4f-c8762c861a8a.png" width="200"></img>

위 예시는 집청소를 동기적으로 실행한 결과입니다. 빨래를 완료하고 나서야 설거지를 실행하네요    
개발을 하다 보면 작업이 순차적으로 진행돼야 할 때도 있지만 위 예시처럼 집청소 같은 작업을 할 때는 `비순차적`으로 진행이 돼야 할 때도 있습니다.

- #### 집청소 비동기
```JSX
React.useEffect(() => {
    async function start() {
        laundry();
        dishes();
    }

    start();
}, []);

const laundry = async () => {
    console.log("빨래 시작");

    var percent = 0;
    while (percent < 101) {
        await console.log(`빨래 ${percent}% 완료`)
        percent += 20;
    }
}

const dishes = async () => {
    console.log("설거지 시작");

    var percent = 0;
    while (percent < 101) {
        await console.log(`설거지 ${percent}% 완료`)
        percent += 20;
    }
}
```

<br />
<img src="https://user-images.githubusercontent.com/68521148/154076503-0fea1e9d-6bb6-4cde-bb93-a2af190d690e.png" width="200"></img>

빨래 행위(while문)를 할 때 await을 사용해 부모에게 주도권을 넘겨주어 dishes() 함수를 호출해 동시에 작업을 진행시켰습니다.
빨래를 돌려두고 설거지를 병행할 순 있지만 설거지를 하면서 방청소는 병행할 수 없습니다.    

설거지를 다 끝낸후 방청소를 시작해 봅시다.

- #### 설거지 종료 후 방청소 시작
```JSX
React.useEffect(() => {
    async function start() {
        laundry();
        await dishes();
        room();
    }

    start();
}, []);

const laundry = async () => {
    console.log("빨래 시작");

    var percent = 0;
    while (percent < 101) {
        await console.log(`빨래 ${percent}% 완료`)
        percent += 20;
    }
}

const dishes = async () => {
    console.log("설거지 시작");

    var percent = 0;
    while (percent < 101) {
        await console.log(`설거지 ${percent}% 완료`)
        percent += 20;
    }
}

const room = async () => {
    console.log("방청소 시작");

    var percent = 0;
    while (percent < 101) {
       await console.log(`방청소 ${percent}% 완료`)
        percent += 20;
    }
};
```

