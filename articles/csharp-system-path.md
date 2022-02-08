# Csharp System Path

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
