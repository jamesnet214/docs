# AspNetCore EnableCors

## 컨트롤러 Attribute
> 컨트롤러에서 Attribute 추가

```csharp
[ApiController]
[EnableCors("MyPolicy")]
[Route("api/[controller]")]
public class AccountController : ControllerBase
{

}
```
