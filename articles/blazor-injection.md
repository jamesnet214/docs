##  Dependency Injection in Blazor

이 리포지토리는 Blazor Injection에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

## Contents
- [Dependency Injection](#dependency-injection)
- [DI Service 구성](#di-service-구성)

<br />

## Dependency Injection

종속성 주입은 느슨하게 결합된 응용 프로그램 디자인을 만드는 데 도움이 되는 디자인 패턴으로 더 나은 유지 관리 가능성, 테스트 가능성 및 재사용성을 제공합니다.
- Blazor는 기본적으로 Dependency Injection을 지원합니다.
- Blazor App에서 이미 내장된 서비스를 컴포넌트에 주입시켜 사용할 수도 있고, 직접 서비스를 만들어서 사용할 수도 있습니다.

<br />

## DI Service 구성
Blazor의 DI 시스템은 [ASP.NET Core DI 시스템](https://docs.microsoft.com/ko-kr/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1)을 기본으로 합니다. DI Service는 생명주기에 따라 구성할 수 있습니다.

|Method|Description|
|:----|:-----------|
|Singleton|서비스의 단일 인스턴스를 생성합니다. 이 서비스가 필요한 모든 구성 요소는 인스턴스에 대한 참조를 받습니다.|
|Transient|서비스가 필요할 때마다 서비스의 새 인스턴스를 생성합니다.|
|Scoped|클라이언트의 Request 시작부터 Response 종료까지 유지되며, 연결되는 각 클라이언트마다 존재합니다.|

<br />

## References
- [Blazor Tutorial - Dependency Injection](https://blazor-tutorial.net/dependency-injection)
- [Dependency injection in ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1)

<br />
