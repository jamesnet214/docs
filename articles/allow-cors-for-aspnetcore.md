# AspNetCore EnableCors

외부 클라이언트로 부터 크로스도메인(CORS) 정책을 허용하기 위해서는 각각의 컨트롤러에 **EnableCors** 어트리뷰트가 추가되어야 합니다.

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
