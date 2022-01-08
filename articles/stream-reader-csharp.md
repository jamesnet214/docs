# C# StreamReader


File
```

```

URL
```
var webRequest = WebRequest.Create(@"https://raw.githubusercontent.com/devncore/devncore-official/main/data/menus/articles.yml");

using (var response = webRequest.GetResponse())
using (var content = response.GetResponseStream())
using (var reader = new StreamReader(content))
{
    var strContent = reader.ReadToEnd();

    var deserializer = new DeserializerBuilder()
               .WithNamingConvention(CamelCaseNamingConvention.Instance)
               .Build();

    var result = deserializer.Deserialize<List<ArticleMenuModel>>(strContent);
}
```
