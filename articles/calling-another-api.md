## AspNetCore 컨트롤러에서 외부 API 호출 방법

이 리포지토리는 AspNetCore 컨트롤러에서 외부 API를 호출하는 방법을 소개합니다.

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

클라이언트는 CORS(크로스 도메인 제한) 정책 때문에 외부에서 제공되는 API 사용이 불가능한 경우가 있습니다. 만약 여러분이 API 서버의 소유자라면 CORS 정책을 허용하도록 하거나 클라이언트에서 프록시 서버를 두어 해결할 것입니다.

하지만 클라이언트 배포환경이 별도의 프록시 포트를 열 수 없는 환경이라면 어떻게 해야할까요?

AspNetCore API 컨트롤러에서 외부 API를 호출해야 합니다.

#### 외부 GET API 호출 예
```csharp
var response = client.GetAsync("https://github.com/login/auth/access_token");
response.Wait();
```

이와 같이 서버 컨트롤러 영역에서 다시한번 웹 API를 호출하여 중간 연결고리를 만들어야 합니다.

POST 형식 호출도 크게 다르지 않습니다.

#### 외부 POST API 호출 예
```csharp
HttpClient client = new HttpClient();

var values = new Dictionary<string, string>
{
    { "code": "000000" },
    { "key", "111111" }
}

var content = new FormUrlEncodedContent(values);
var response = await client.PostAsync("https://github.com/login/auth/access_token", content);
var responseString = await response.Content.ReadStringAsync();
```
