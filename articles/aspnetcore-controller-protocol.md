## AspNetCore Controller

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
