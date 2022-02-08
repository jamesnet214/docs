## Csharp System Path

이 리포지토리는 Csharp System Path 에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />


## 현재 시스템(Current) 유저 폴더
```csharp
using System;

string userRoot = Environment.GetEnvironmentVariable("USERPROFILE");
```

## 다운로드 폴더
다운로드 폴더는 userRoot와 조합하여 만들 수가 있습니다.
```
using System;

string userRoot = Environment.GetEnvironmentVariable("USERPROFILE");
string downloadRoot = $@"{userRoot}/Downloads";
```
