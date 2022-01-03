# React Markdown Viewer

## 내용
- [x] 1. npm 설치
- [x] 2. Component 생성
- [x] 3. Markdown 파일 연결

### 1. Markdown View
가장 먼저 Markdown 뷰어를 구현합니다.

#### 1.1. Install packeages
uiw사의 React markdown 패키지를 설치합니다.
```
npm install @uiw/react-md-editor;
```

#### 1.2. Create component
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
