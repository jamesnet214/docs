작업 순서
- [x] 1. Markdown View
- [x] 2. Environment

### 1. Markdown View
가장 먼저 Markdown 뷰어를 구현합니다.

#### 1.1. Install packeages
uiw사의 React markdown 패키지를 설치합니다.
```
npm install @uiw/react-md-editor;
```

####1.2. Create component
```
// root/src/components/md/MarkdownViewer.jsx

import React from "react";
import MDEditor from "@uiw/react-md-editor";

export default function MarkdownView(props) {
    const { mdName } props;
    const [markdown, setMarkdown] = React.useState('');
        .then(r) => r.text())
        .then(text => setPost(text);
    return <MDEditor.Markdown source={markdown}/>
}
```

### 2. Create Environment
```
.env.development
.env.production
```
로컬 포트 설정
```
PORT=3000
```

### 3. Portal
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
