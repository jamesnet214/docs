## YAML 파일 C# 변환

이 리포지토리는 YAML 파일 C# 변환에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

## Nuget 패키지 설치 및 Using 정보
- YamlDotNet Nuget 설치
- using YamlDotNet.Serialization;
- using YamlDotNet.Serialization.NamingConventions;

| Nuget 설치 | Yaml Using |
|:----------:|:----------:|
| ![image](https://user-images.githubusercontent.com/76234292/148646402-19d302c2-30ce-47e7-9c31-1da014fc550e.png) | ![yamlusing](https://user-images.githubusercontent.com/76234292/148657700-34fc264c-61e9-479c-b334-78d426375542.PNG)

<br />

### Yaml 파일 C# 변환하기
```
var deserializer = new DeserializerBuilder()
           .WithNamingConvention(CamelCaseNamingConvention.Instance)
           .Build();

var result = deserializer.Deserialize<List<ArticleMenuModel>>(strContent);

```

### C# List Yaml 변환하기

```C#
string yaml;
List<Model> datas;

var serializer1 = new SerializerBuilder()
    .WithNamingConvention(CamelCaseNamingConvention.Instance)
    .Build();

yaml = serializer1.Serialize(datas);

```

TBD...

