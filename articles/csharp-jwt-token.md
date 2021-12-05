# csharp-jwt-token
이 문서는 C#에서 Jwt Token을 생성과 유효성 체크에 대한 내용을 다루고 있습니다.

## Orverview

TBD...
## JwtToken 생성
다음은 C#에서 JwtToken을 생성하는 방법입니다.
```
public string GenerateToken(string userId)
{
    var mySecret = "asdv234234^&%&^%&^hjsdfb2%%%";
    var mySecurityKey = new SymmetricSecurityKey(Encoding.ASCII.GetBytes(mySecret));

    var myIssuer = "http://mysite.com";
    var myAudience = "http://myaudience.com";

    var tokenHandler = new JwtSecurityTokenHandler();
    var tokenDescriptor = new SecurityTokenDescriptor
    {
        Subject = new ClaimsIdentity(new Claim[]
        {
    new Claim(ClaimTypes.NameIdentifier, userId.ToString()),
        }),
        Expires = DateTime.UtcNow.AddDays(7),
        Issuer = myIssuer,
        Audience = myAudience,
        SigningCredentials = new SigningCredentials(mySecurityKey, SecurityAlgorithms.HmacSha256Signature)
    };

    var token = tokenHandler.CreateToken(tokenDescriptor);
    return tokenHandler.WriteToken(token);
}
```

## 참고 문서
- [생성과 유효성체크 심플 소스코드](https://jasonwatmore.com/post/2021/06/02/net-5-create-and-validate-jwt-tokens-use-custom-jwt-middleware)
- [C#에서 JWTToken 생성 및 유효성 체크](https://www.c-sharpcorner.com/article/jwt-validation-and-authorization-in-net-5-0/)
