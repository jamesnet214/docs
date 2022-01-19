##  EntityFramework-Sqlite
이 리포지토리는 EntityFramework-Sqlite의 Migration 관련된 정보를 기술한 리포지토리입니다. <br />
  
<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>

| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

## Migration 진행정보

#### ASP.NET Core 환경에서 EntityFrameworkCore Sqlite 설치 순서
- Install NugetPackage: **`Microsoft.EntityFrameworkCore.Sqlite`**, **`Microsoft.VisualStudio.Web.CodeGeneration.Design`**
- add-migration CreateIdentitySchema -OutputDir Data\Migrations
- update-database
