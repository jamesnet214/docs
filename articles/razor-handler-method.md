## razor-handler-method

- `OnGet()`
- `OnPost()`
- `OnGetAsync()`
- `OnPostAsync()`

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
