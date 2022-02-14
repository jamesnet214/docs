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

먼저 async/await이 필요한 상황을 예시로 알아봅시다.
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

#### 결과
<img src="https://user-images.githubusercontent.com/68521148/153867801-9ac9b573-4ec6-4c2d-bb4f-c8762c861a8a.png" width="200"></img>

위 예시는 집청소를 동기적으로 실행한 결과입니다. 빨래를 완료하고 나서야 설거지를 실행하네요    
개발을 하다 보면 작업이 순차적으로 진행돼야 할 때도 있지만 위 예시처럼 집청소 같은 작업을 할 때는 `비순차적`으로 진행이 돼야 할 때도 있습니다.
