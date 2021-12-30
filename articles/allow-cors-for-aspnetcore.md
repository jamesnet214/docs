# AspNetCore EnableCors

외부 클라이언트로 부터 크로스도메인(CORS) 정책을 허용하기 위해서는 각각의 컨트롤러에 **EnableCors** 어트리뷰트가 추가되어야 합니다.

## 컨트롤러
**EnableCors 어트리뷰트를 추가합니다.** 어트리뷰트 선언 부분의 이름은 반드시 필수(Require)로 입력합니다.

```csharp
[ApiController]
[EnableCors("MyPolicy")]
[Route("api/[controller]")]
public class AccountController : ControllerBase
{

}
```
**아직 Cors 프로필이 없다면** Startup.cs 파일의 Configs 설정 부분에서 Proxy 관련 설정을 추가합니다.

```
// startup.cs

var MyAllowSpecificOrigins = "_devncoreOrigins";

...

builder.Services.AddCors(options => 
{
    options.AddPolicy(name: MyAllowSpecificOrigins,
        builder => 
        {
            builder.WithOrigins("https://devncore.org",
                "https://cbt.devncore.org");
        });
});

...

app.UseCors(MyAllowSpecificOrigins);
```

TBD...
