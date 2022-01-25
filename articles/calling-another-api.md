## AspNetCore Controller에서 외부 API 호출 방법

이 리포지토리는 AspNetCore Controller에서 외부 API를 호추ㄹ하는 방법을 소개합니다.

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

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

```csharp
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
최종적으로 `app.UseCors(MyAllowSpecificOrigins);`를 통해 지정된 도메인의 API 연결을 특별하게 허용할 수 있습니다.

> CORS와 관련된 정책, 기술들은 SSO(Single Sign On)인증방식 또는 외부 앱(Web, App 등)과의 프로토콜에 있어 핵심적인 정책입니다.

## 한번에 Cors 허용하기
특정 URL의 크로스 도메인 제한 여부를 한번에 허용할 수도 있습니다.
```
app.UseCors(builder => {
    builder.WithOrigins("https://localhost:3000")
        .AllowAnyHeader()
        .AllowAnyMethod()
        .AllowCredentials();
}
```
