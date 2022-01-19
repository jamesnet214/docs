## AspNetCore API

이 리포지토리는 AspNetCore API 프로젝트 구현 방법을 설명합니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />


## Repository

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

## Get
```

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


## Post
```

```
## Put

## Delete

## References
- [code-maze](https://code-maze-com/net-core-web-development-part6/)
