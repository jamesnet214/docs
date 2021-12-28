# EntityFramework-Sqlite

## Migration
#### ASP.NET Core 환경에서 EntityFrameworkCore Sqlite 설치 순서
1. Install NugetPackage: **`Microsoft.EntityFrameworkCore.Sqlite`**, **`Microsoft.VisualStudio.Web.CodeGeneration.Design`**
1. add-migration CreateIdentitySchema -OutputDir Data\Migrations
1. update-database
