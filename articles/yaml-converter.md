# YAML 파일 C# 변환


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

