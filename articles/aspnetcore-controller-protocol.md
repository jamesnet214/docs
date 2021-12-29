## AspNetCore Controller

## Get
```

[HttpGet("users")]
public async Task<IActionResult> Users()
{
    try 
    {
        var users = getUsers();
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

## Put

## Delete
