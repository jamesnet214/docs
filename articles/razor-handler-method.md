## razor-handler-method
Razor Pages에서 Handler Method는 요청의 결과로써 자동적으로 수행됩니다. Handler Method는 반드시 `public`이어야 하며, `void`, `Task`, `IActionResult`를 return 값으로 할 수 있습니다.

```csharp
public class IndexModel : PageModel
{
    public string Message { get; set; }
    public void OnGet()
    {
        Message = "Get used";
    }
    public void OnPost()
    {
        Message = "Post used";
    }
}
```

- `OnGet()`
- `OnPost()`
- `OnGetAsync()`
- `OnPostAsync()`

## Named Handler Methods

## Parameter
`asp-route-[parameter name]` (ex. asp-route-query, asp-route-id, asp-route-device)  
action, controller, page 등 몇 가지 키워드는 사용불가

#### `.cshtml`
```html
<a asp-page-handler="SearchDevice" asp-route-device="USB">
    <div style="background-color: #6FD2E8">일반 USB</div>
</a>
```

#### `.cshtml.cs`
```csharp
public void OnGetSearchDevice(string device)
{
    //
}
```

## Reference
https://www.learnrazorpages.com/razor-pages/handler-methods
https://codingblast.com/asp-net-core-razor-pages-handlers/
