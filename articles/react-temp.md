# React Portal Framework (RPF)
이 아티클에서는 RPF 프레임워크를 소개하고 개발 방법에 대한 설명을 다루고 있습니다. 

리액트의 전반적인 소개는 여기 [The Easiest React](https://github.com/devncore/the-easiest-react)에서 보실 수 도 있습니다.
## 내용
- [x] 1. 환경설정(Environment)
- [x] 2. 포트 설정
- [x] 3. SPA
- [x] 4. ReactDOM
- [x] 5. Portal
- [x] 6. Route

## 1. Environment
React는 환경정보를 **Environment** 파일 형식으로 관리합니다. 아래는 각 환경 별 파일 이름 규칙입니다.

```
.env.development
.env.test
.env.production
```
그리고 각각의 .env 파일은 빌드 과정에서 자동으로 매핑됩니다.
| 개발 | 테스트 | 운영 배포 |
|:---:|:---:|:---:|
| Development | Test | Production |
| npm run start | npm run test | npm run deploy | 

## 2. 포트 설정
개발단계에서 포트를 지정할 수 있습니다.

```
// .env.development
PORT=3000
```

## 3. SPA (Single Page Application)
> SPA에 대한 자세한 설명은 [여기](https://github.com/devncore/docs/articles/single-page-application)에서 확인하실 수 있습니다.  

React는 SPA 단일 페이지 애플리케이션 구조로서 다음 파일을 기점으로 웹이 동작됩니다.

```
public/index.html
```
기준이 되는 이 파일의 위치는 public (react 구조에서 유일하게 정적 파일경로를 허용하는 루트) 안에 포함되어있어야 합니다.

index.html 파일은 기본적인 html 구조를 포함하고 있으며 **body** 태그 안에 React 객체를 대체할 약속된 DOM 영역을 포함해야 합니다.

```
<body>
    <div id="root"></div>
</body>
``` 

## 4. ReactDOM 
- index.js

## 5. Portal
Route를 관리하는 메인격인 페이지입니다.

react-router 패키지 설치
```
npm install react-router
```

```
// root/src/apps/Portal.js

import { Route } from "react-router";
import MarkdownViewer from "../components/md/MarkdownViewer";

export default function Portal(props) {
    return (
        <div>
            <Route path={process.env.PUBLIC_URL + '/md'} render={() => <MarkdownViewer mdName="Rㄷㅁ읃.md"/>}/>
        </div>
    );
}
```

### 4. Route
index.js 페이지에서 BrowserRouter 컴포넌트를 최상위 Root에 추가하고 Portal 페잊ㅣ를 자식으로 포함시킵니다.

```
npm install react-router-dom
```

```
// root/src/index.js

import React from "react";
import ReactDOM from "react-dom";
import "./index.css";
import reportWebVitals from "./reportWebVitals";
import Portal from "./apps/Portal.js";

ReactDOM.render(
    <BrowserRouter>
        <Portal/>
    </BrowserRouter>
);

reportWebVitals();
```
