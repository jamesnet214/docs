## React Express 서버

이 리포지토리는 React에서 Express 서버 구축에 대한 내용을 설명합니다.   

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

## npm 설치
node 환경에서 로컬 서비스를 만들기 위한 서버 모듈인 `express`를 설치합니다.
```
npm install express
```

## Express 구조

#### 서비스 (index.js)
```jsx
const express = require("express");
const router = express.Router();

router.get("/", function(req, res) {
    res.send({
        message: "Hello DevNcore");
    });
});
```

#### 서버 (server.js)
```jsx
const express = require("express");
const app = express();
const api = require("./routes/index");

app.use("/api", api);

const port = 5000;
app.listen(port, () => console.log(`Listening on port ${port}`));
```

#### node 서버 구동
(src 폴더를 기준으로 합니다.)
```
node ./server/server.js
```

## 프록시 연결
#### npm 설치
```
npm install http-proxy-middleware
```
#### setupProxy.js
파일명과 위치는 약속된 경로와 이름입니다. (http-proxy-middleware) 
```jsx
const { createProxyMiddleware } = require("http-proxy-middleware");

module.exports = function(app) {
    app.use(
        "/api",
        createProxyMiddleware({
            target: "http://localhost:5000",
            changeOrigin: true,
        })
    );
};
```
