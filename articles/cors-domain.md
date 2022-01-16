## CORS 도메인 정책

이 리포지토리는 CORS 도메인 정책에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### CORS란?
> 교차 출처 리소스 공유(Cross-Origin Resource Sharing, CORS)

**CORS** (교차 출처 자원 공유)는 웹 페이지 상의 제한된 리소스를 최초 자원이 서비스된
도메인 밖의 다른 도메인으로부터 요청할 수 있게 허용하는 구조이다. 
CORS는 교차 출처 요청을 허용하는 것이 안전한지 아닌지를 판별하기 위해 브라우저와 서버가
상호 통신하는 하나의 방법을 정의한다.
웹 애플리케이션은 리소스가 자신의 출처(도메인, 프로토콜, 포트)와 다를 때 교차 출처 HTTP 요청을 실행합니다.

### CORS 사용목적
예전 프로젝트들은 대부분 하나의 서버에서 브라우저의 모든 요청을 처리하여 문제가 없었지만
클라이언트와 API가 분리되면서 도메인이 서로 달라져 보안의 취약점 문제가 발생하게 되었습니다.
CORS의 HTTP 헤더를 사용하여 한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하여 브라우저와 서버 간의 안전한 교차 출처 요청 및 데이터 전송을 지원이 가능합니다.

### CORS 정책 적용방법

> API Program.cs 에서 CORS 정책 적용

```
app.UseCors(builder =>
{
    builder.WithOrigins("https://localhost:3000")
        .AllowAnyHeader()
        .AllowAnyMethod()
        .AllowCredentials();
});
```

> Client 에서 CORS 정책 적용
```
const headers = {
        headers: {
            "Content-Type": "application/json",
            'Access-Control-Allow-Origin': '*',
            'Access-Control-Allow-Credentials': '*',
            'Access-Control-Allow-Methods': '*',
            "REACT-PORTAL-SESSION": "TEMP0106"
        }
    };
```

### CORS 적용 전 적용 후

| 적용 전 | 적용 후 |
|:--------:|:------:|
| ![cors1](https://user-images.githubusercontent.com/52397976/148246993-c81b1217-308b-4614-9aba-cd6b465131ee.png) | ![cors2](https://user-images.githubusercontent.com/52397976/148247021-dfa01941-3379-42a3-ac29-4aa5af71de43.png) | 
| CORS 크로스 도메인 정책으로 인한 에러 발생 | 외부 API 정상으로 호출됨 |
<br />

### CORS 정책 Headers 옵션정보

> Access-Control-Allow-Origin

리턴된 리소스에는 다음 구문과 함께 하나의 Access-Control-Allow-Origin 헤더가 있을 수 있습니다.
Access-Control-Allow-Origin 은 단일 출처를 지정하여 브라우저가 해당 출처가 리소스에 접근하도록 허용합니다. 또는 자격 증명이 없는 요청의 경우 "*" 와일드 카드는 브라우저의 origin에 상관없이 모든 리소스에 접근하도록 허용합니다.

<br />

> Access-Control-Allow-Headers

preflight request 에 대한 응답으로 Access-Control-Allow-Headers 헤더가 사용됩니다. 실제 요청시 사용할 수 있는 HTTP 헤더를 나타냅니다.

<br />

> Access-Control-Allow-Methods

Access-Control-Allow-Methods (en-US) 헤더는 리소스에 접근할 때 허용되는 메서드를 지정합니다. 이 헤더는 preflight request에 대한 응답으로 사용됩니다.

<br />

> Access-Control-Allow-Credentials

Access-Control-Allow-Credentials 헤더는 credentials 플래그가 true일 때 요청에 대한 응답을 표시할 수 있는지를 나타냅니다. preflight request에 대한 응답의 일부로 사용하는 경우, credentials을 사용하여 실제 요청을 수행할 수 있는지를 나타냅니다. simple GET requests는 preflighted되지 않으므로 credentials이 있는 리소스를 요청하면, 이 헤더가 리소스와 함께 반환되지 않습니다. 이 헤더가 없으면 브라우저에서 응답을 무시하고 웹 컨텐츠로 반환되지 않습니다.



