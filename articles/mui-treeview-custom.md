# MUI TreeView Customizing
MUI TreeView을 통한 커스터마이징을 **Functional Component** 방식으로 설명합니다.

Hierachy 데이터를 기반으로 만들 수 있습니다.
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

