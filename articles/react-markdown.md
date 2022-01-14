## React Markdown Viewer

이 리포지토리는 React Markdown Viewer에 대해 기술한 리포지토리입니다. <br />
이 리포지토리는 DevNcore팀이 관리하고 있습니다.  

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

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
