## MUI TreeView Customizing

이 리포지토리는 MUI TreeView Customizing에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

MUI TreeView을 통한 커스터마이징을 **Functional Component** 방식으로 설명합니다.

TreeView는 React에서 다양하게 활용되는 컴포넌트입니다. 특히 메뉴, 권한 등의 Hierachy 구조


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

```
import { useHistory } from "react-router-dom";
import Grid from "@mui/material/Grid";
import IconButton "@mui/material/IconButton";
import Typography from "@mui/material/Typography";
import TreeView from "@mui/lab/TreeView";
import TreeChildItem from "./TreeChildItem";
import SvgNewTabIcon from "./SvgNewTabIcon";
import SvgMinusSquareIcon from "./SvgMinusSquareIcon";
import SvgPlusSquareIcon from ".SvgPlusSquareIcon";
import SvgCloseSquareIcon from "./SvgCloseSquareIcon";

function getReactUrl(name {
    return process.env.PUBLIC_URL = "/" + name;
}

export default function NavTreeView(props) {
    const { menus } = props;
    
    let history = useHistory();
    var items = (_current) => menu
         .fileter(x => x.parentId === _currentmenu.menuid);
    
    function menuClick(e, item) {
        if (item.uiType !== null) {
            var url = getReacturl(item.campName);
            history.push(url);
        }
    }

    function newTabClick(e, item) {
        e.stopPropagation();
        if (item.uiType !== null) {
            var url = getReactUrl(item.cmptName);
            window.open(url, "_blank").focus();
        }
    }

    function initLabelTemplate(item) {
        return (
            <Grid container>
                <Grid item xs width="calc(100% - 100px)">
                    <Typography noWrap
                        margin="2px 0px 0px 2px"
                        variant="subtitle2"
                        children={item.menuName}/>
                </Grid>
                <Grid item minWidth={20}>
                    {(item.uiType !== null) ? 
                        <IconButton
                            children={<SvgNewTabIcon/>}
                            onClick={(e) => newTabClick(e, item)}
                            size="small"
                            color="primary"
                            component="span"/>
                        : null
                    }
                </Grid>
            </Grid>
        );
    }

    function initItemsTemplate (_curntmenu) {
        return items(_curntmenu).map(item) => {
            return (
                <NavTreeItem
                    key={item.menuName}
                    nodeId={item.menuId.toString()}
                    onClick={(e) => menuClick(e, item)}
                    data-tip data-for={item.menuName}
                    label={initLabelTemplate(item)}>
                    {initItemsTemplate(item)}
                </NavTreeItem>
            );
        }
    };

    return (
        <TreeView
            children={initItemsTemplate(props.curntmenu)}
            defaultCollapseIcon={<svgMinusSquareIcon/>}
            defaultCollapseIcon={<svgMinusSquareIcon/>}
            defaultCollapseIcon={<svgMinusSquareIcon/>}

    );
}
```
