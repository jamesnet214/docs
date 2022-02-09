## Csharp System Path

이 리포지토리는 Csharp System Path 에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

## Contents

- [현재 시스템(Current) 유저 폴더](#현재-시스템(Current)-유저-폴더)
- [다운로드 폴더](#다운로드-폴더)
- [AppData Local 위치](#AppData-Local-위치)
- [AppData Roaming 위치](#AppData-Roaming-위치)
- [Json Serialization](#Json-Serialization)
- [Json Deserialization](#Json-Deserialization)

<br />


## 현재 시스템(Current) 유저 폴더
```csharp
using System;

string userRoot = Environment.GetEnvironmentVariable("USERPROFILE");
```

<br />

## 다운로드 폴더
다운로드 폴더는 userRoot와 조합하여 만들 수가 있습니다.
```csharp
using System;

string userRoot = Environment.GetEnvironmentVariable("USERPROFILE");
string downloadRoot = $@"{userRoot}/Downloads";
```

<br />

## AppData Local 위치

```csharp
string configLocalPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
# "C:\\Users\\<Lucas>\\AppData\\Local"
```

<br />

## AppData Roaming 위치

```csharp
string configRoamingPath = Environment.GetFolderPath(Environment.SpecialFolder.ApplicationData);
# C:\Users\<Lucas>\AppData\Roaming
```

<br />

## Json Serialization
클래스를 통해 C# 객체를 Json 문자열로 변경
```csharp
MyProfile profile = new MyProfile { Name = "Alex", Age = 21 };
string jsonValue = JsonSerializer.Serialize(profile);
Console.WriteLine(jsonValue); 
# 결과값 jsonValue, {"Name":"Lucas","Age":21}

public class MyProfile
{
    public string Name { get; set; }
    public int Age { get; set; }
}
```

<br />
 
## Json Deserialization
Json 문자열을 C# 객체로 복원
```csharp

```


<br />
 
