## C# StreamReader

이 리포지토리는 C# StreamReader에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### StreamReader 이란?
TBD...

### Assembly Resource File
```csharp
private T DeserializeObject<T>(string resName)
{
    var assembly = Assembly.GetExecutingAssembly();
    var resourceName = resName;

    using (Stream stream = assembly.GetManifestResourceStream(resourceName))
    using (StreamReader reader = new StreamReader(stream))
    {
        string result = reader.ReadToEnd();
        return JsonSerializer.Deserialize<T>(result);
    }
}
```

### URL
```csharp
var webRequest = WebRequest.Create(@"https://raw.githubusercontent.com/devncore/devncore-official/main/data/menus/articles.yml");

using (var response = webRequest.GetResponse())
using (var content = response.GetResponseStream())
using (var reader = new StreamReader(content))
{
    var strContent = reader.ReadToEnd();
}
```
