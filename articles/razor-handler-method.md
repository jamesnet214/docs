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
Razor Pages는 `Named Handler Methods`라는 기능을 포함하고 있습니다. 이 기능을 통해 단일 동사로 여러 메서드를 구체화할 수 있습니다. 페이지에 여러 개의 form이 있을 때 사용할 수도 있으며 각각 다른 결과를 담당합니다. 


```csharp
public class IndexModel : PageModel
{
    public string Message { get; set; } = "Initial Request";
    public void OnGet()
    {
    }
    public void OnPost()
    {
        Message = "Form Posted";
    }
    public void OnPostDelete()
    {
        Message = "Delete handler fired";
    }
    public void OnPostEdit(int id)
    {
        Message = "Edit handler fired";
    }
    public void OnPostView(int id)
    {
        Message = "View handler fired";
    }
}
```

## asp-page-handler
Named Handler Methods를 정의한 후에는 form에서 `asp-page-handler` 속성을 사용하여 연결합니다.
```html
<div class="row">
    <div class="col-lg-1">
        <form asp-page-handler="edit" method="post">
            <button class="btn btn-default">Edit</button>
        </form>
    </div>
    <div class="col-lg-1">
        <form asp-page-handler="delete" method="post">
            <button class="btn btn-default">Delete</button>
        </form>
    </div>
    <div class="col-lg-1">
        <form asp-page-handler="view" method="post">
            <button class="btn btn-default">View</button>
        </form>
    </div>
</div>
<h3 class="clearfix">@Model.Message</h3>
```

### Parameter
- `asp-route-[parameter name]` (ex. asp-route-query, asp-route-id, asp-route-device)  
- action, controller, page 등 몇 가지 키워드는 사용불가

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
- https://www.learnrazorpages.com/razor-pages/handler-methods  
- https://codingblast.com/asp-net-core-razor-pages-handlers/
