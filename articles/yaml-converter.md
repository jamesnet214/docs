# YAML 파일 C# 변환


## Nuget 패키지 설치 및 Using 정보
- YamlDotNet Nuget 설치
- using YamlDotNet.Serialization;
- using YamlDotNet.Serialization.NamingConventions;

### YAML파일 C# 변환하기
```
var deserializer = new DeserializerBuilder()
           .WithNamingConvention(CamelCaseNamingConvention.Instance)
           .Build();

var result = deserializer.Deserialize<List<ArticleMenuModel>>(strContent);

```

### C# 정보 YAML 변환하기

```C#
string yaml;
List<ArticleMenuModel> datas;

var serializer1 = new SerializerBuilder()
    .WithNamingConvention(CamelCaseNamingConvention.Instance)
    .Build();

yaml = serializer1.Serialize(datas);

```

TBD...

