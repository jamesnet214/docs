# C# StreamReader

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
