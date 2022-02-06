## AutoComplete 기능

이 리포지토리는 AutoComplete 기능에 대하여 설명합니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br>

### 브라우저별 현황
- [ ] Chrome: 3.14버전부터 이 기능을 제어하는 것은 유저 입장에서 불합리하다는 결론을 내려 기능을 폐기함.
- [x] Edge: 
- [x] Safari: 
<br>

### 기능 제거
jQuery를 통한 `autocomplete` off 처리

```jsx
<script src="./script/jquery.min.js"></script>
<script>
    $(document).ready(function(){
        $('input').attr("autocomplete", "off");
    });
</script>
```
