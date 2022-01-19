## AspNetCore API

이 리포지토리는 AspNetCore API 프로젝트 구현 방법을 설명합니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

## 내용
- [프로젝트 생성](#프로젝트-생성)
- [Router](#Router)
- [HttpGet](#HttpGet)
- [RepositoryBase](#RepositoryBase)

## 프로젝트 생성
프로젝트 생성은 Microsoft Docs(구 MSDN)에서 제공하는 자습서를 [참고](https://microsoft.com)해주시기 바랍니다. 프로젝트 생성 방법에 대해 아주 상세하게 설명되어 있습니다.
#### 제공 환경
- Visual Studio
- Visual Studio Code
- Visual Studio Mac

## HttpGet
HttpGet Attribute를 통해 Get 타입의 프로토콜 메서드를 선언할 수 있습니다.
```csharp
[HttpGet("users")]
public async Task<IActionResult> Users()
{
    try 
    {
        var users = _repository.User.GetUsers();
        _logger.LogInfo("Returned all users from database.");
        return Ok(owners);
    }
    catch (Exception)
    {
        _logger.LogError($"Something went wrong inside GetUsers action: {ex.Message}");
        return StatusCode(500, "Internal server error");
    }
}
```

## RepositoryBase

```
public interface IUserRepository
{
    IEnumerable<User> GetUsers();
}
```

```
public class UserRepository : RepositoryBase<User>, IUserRepository
{
    public UserRepository(SomeContext someContext)
        :base(someContext)
    {
        return FindAll()
            .OrderBy(ow => ow.Name)
            .ToList();
    }
}
```


## Post
```

```
## Put

## Delete

## References
- [code-maze](https://code-maze-com/net-core-web-development-part6/)
