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
```
