## Swagger UI 설정

### Swagger 란?

스웨거(Swagger)는 개발자가 REST 웹 서비스를 설계, 빌드, 문서화, 소비하는 일을 도와주는 대형 도구 생태계의 지원을 받는 오픈 소스 소프트웨어 프레임워크입니다.
스웨거 UI 도구를 통해 스웨거를 식별하며 스웨거 툴셋에는 자동화된 문서화, 코드 생성, 테스트 케이스 생성 지원이 포함됩니다.

Swagger Rest API 의 자세한 정보는 [여기](https://swagger.io/solutions/api-documentation/)를 눌러주세요.
<br />

### Swagger 접속방법

| Swagger 접속정보 |
|:--------:|
| ![swag](https://user-images.githubusercontent.com/76234292/148257279-349c9d02-2c89-42f4-affc-8d67d2d0154d.png) |  
| https://localhost:5451/swagger/index.html |

<br />

### Swagger Nuget 설치 정보

| Nuget 설치 | Nuget 설치완료 |
|:--------:|:------:|
| ![image](https://user-images.githubusercontent.com/76234292/148259101-c6c1d192-c66e-4488-b039-e76c42d78c82.png) | ![image](https://user-images.githubusercontent.com/76234292/148258380-d418a5ab-27e3-4dcb-adc5-f2bffbe61ed4.png) | 
| Swashbuckle.AspNetCore 검색 후 설치 | Nuget 설치완료 정보 |

<br />

### Swagger 소스 적용

> API Swagger 소스 적용정보

```
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}
```

```
builder.Services.AddSwaggerGen();
```

<br />

