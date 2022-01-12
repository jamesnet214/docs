## Git Branch

**Branch란?** <br />
모든 버전 관리 시스템은 브랜치를 지원하는데 개발을 하다 보면 코드를 여러 개로 복사해야 하는 일이 자주 생긴다. 이 때 코드를 통째로 복사하고 나서 원래 코드와는 상관없이 독립적으로 개발을 진행할 수 있는데, 이렇게 독립적으로 개발하는 것이 브랜치다.

**Branch 조회**

```
git branch
```

**Branch 생성**   git branch <브랜치명>

```
git branch lucas
```

**Branch 전환**   git checkout <브랜치명>

```
git checkout lucas
```

**Branch 병합**   git merge <병합할 브랜치명>

```
git checkout main
git merge lucas
```

**Branch 삭제**   git branch -d <브랜치명>

```
git branch -d lucas
```

## Git Push Error
아래의 메세지는 git push 명령어를 실행 하였을 때 나는 오류 메세지이다.
원인은 원격저장소 이름을 입력하지 않았기 때문이며 원격저장소 이름을 확인후 원격저장소명을 명시해 Push 한다.
```
fatal: The current branch lucas has no upstream branch. <br />
To push the current branch and set the remote as upstream, use
git push --set-upstream origin lucas
```

**현재 저장된 원격저장소명 확인**
```
git remote -v
```

**원격저장소명을 명시하여 push**   git push <원격저장소명> <브랜치명>
```
git push origin lucas
```
