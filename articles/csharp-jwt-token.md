# JWT 이해 및 C#을 통한 구현방법
### 목적
본문은 **JWT**를 처음 접하거나 이것을 사용하기 위한 개념과 기술에 대해 전반적으로 설명합니다. 그리고 C#을 통한 JWT 구현 방법도 제공하고 있습니다.

### 내용
- [JWT 구조](#jwt-구조)
- [Header](#header)
- [Payload](#payload)
- [Signiture](#signiture)
- [JWT 생성](#jwt-생성)
- [JWT Validation 체크](#jwt-validation-)

## JWT 구조
JWT는 3개의 구조로 이루어져 있는 Base64 형태의 암호화된 인증 체계 값입니다.
- Header
- Payload
- Signiture

![image](https://user-images.githubusercontent.com/52397976/144880256-9e3f3258-694b-444e-9690-c7e4da787067.png)


#### Header
```
{
    "alg": "HS256",
    "typ": "JWT"
}
```

#### Payload
```
{
    "sub": "1234567890",
    "name": "John Doe",
    "admin": true
}
```
#### Signiture
```
HMAC_SHA256(
    secret,
    base64urlEncoding(header) + '.' +
    base64urlEncoding(payload)
)
```

## JWT 생성
다음은 C#에서 JwtToken을 생성하는 방법입니다.

```csharp
public string GenerateToken(ApplicationUser user)
{
    // generate token that is valid for 7 days
    var tokenHandler = new JwtSecurityTokenHandler();
    var key = Encoding.ASCII.GetBytes(mySecret);
    var tokenDescriptor = new SecurityTokenDescriptor
    {
        Subject = new ClaimsIdentity(new[] { new Claim("id", user.Id.ToString()) }),
        Expires = DateTime.UtcNow.AddDays(7),
        SigningCredentials = new SigningCredentials(new SymmetricSecurityKey(key), SecurityAlgorithms.HmacSha256Signature)
    };
    var token = tokenHandler.CreateToken(tokenDescriptor);
    return tokenHandler.WriteToken(token);
}
```

## JWT Validation 체크
```csharp
public string ValidateToken(string token)
{
    if (token == null)
        return null;

    var tokenHandler = new JwtSecurityTokenHandler();
    var key = Encoding.ASCII.GetBytes(mySecret);
    try
    {
        tokenHandler.ValidateToken(token, new TokenValidationParameters
        {
            ValidateIssuerSigningKey = true,
            IssuerSigningKey = new SymmetricSecurityKey(key),
            ValidateIssuer = false,
            ValidateAudience = false,
            // set clockskew to zero so tokens expire exactly at token expiration time (instead of 5 minutes later)
            ClockSkew = TimeSpan.Zero
        }, out SecurityToken validatedToken);

        var jwtToken = (JwtSecurityToken)validatedToken;
        var userId = jwtToken.Claims.First(x => x.Type == "id").Value;

        // return user id from JWT token if validation successful
        return userId;
    }
    catch
    {
        // return null if validation fails
        return null;
    }
}
```

## 참고 문서
- [생성과 유효성체크 심플 소스코드](https://jasonwatmore.com/post/2021/06/02/net-5-create-and-validate-jwt-tokens-use-custom-jwt-middleware)
- [C#에서 JWTToken 생성 및 유효성 체크](https://www.c-sharpcorner.com/article/jwt-validation-and-authorization-in-net-5-0/)
