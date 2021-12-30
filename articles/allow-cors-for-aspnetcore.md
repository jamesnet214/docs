# AspNetCore EnableCors

외부 클라이언트로 부터 크로스도메인(CORS) 정책을 허용하기 위해서는 각각의 컨트롤러에 **EnableCors** 어트리뷰트가 추가되어야 합니다.

## 컨트롤러
**EnableCors 어트리뷰트를 추가합니다.**

```csharp
[ApiController]
[EnableCors("MyPolicy")]
[Route("api/[controller]")]
public class AccountController : ControllerBase
{

}
```
어트리뷰트 변수 이름은 Startup.cs Confings 설정 부분에서 정의된 Cors 이름과 동일해야 합니다.

추가된 규칙이 없을 경우 아래와 같이 추가하도록 합니다.

```
// startup.cs
```
