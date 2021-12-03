# Sqlite

## Content
- [Migration](#migration)

## Migration
#### ASP.NET Core 환경에서 EntityFrameworkCore Sqlite 설치 순서
- [ ] **Install NugetPackage**: Microsoft.EntityFrameworkCore.Sqlite, Microsoft.VisualStudio.Web.CodeGeneration.Design
- [ ] add-migration CreateIdentitySchema -OutputDir Data\Migrations
- [ ] update-database
