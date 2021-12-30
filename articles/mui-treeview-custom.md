# MUI TreeView Customizing
MUI TreeView을 통한 커스터마이징을 **Functional Component** 방식으로 설명합니다.

## 컴포넌트
**Hierachy 데이터**를 기준으로 컴포넌트가 설계되었습니다.
```
// DevNcoreTreeView.js

export default function DevNcoreTreeView(props) {
    const { menus } = props;

    return (
        <TreeView
            className={tree}
            defaultCollapseIcon={<SvgCollapseIcon/>}
            defaultExpandIcon={<SvgExpandIcon/>}
            defaultEndIcon={<SvgEndIcon/>}/>
    );
}
```

## 아이콘
MUI TreeView는 기본적으로 3개의 아이콘을 확장할 수 있도록 프로퍼티로 제공합니다.
| 이름 | 설명 |
|:----|:-----|
| defaultCollapseIcon | 하위 자식 노드 영역을 숨기는 Collapse 기능 |
| defaultExpandIcon | 하위 자식 노드 영역을 펼치는 Expand 기능 |
| defaultEndIcon | 더이상 하위 자식 노드 영역이 없을 때 대체되는 아이콘 |
