# JWT 이해 및 C#을 통한 구현방법
> **JWT**에 대한 전반적인 개념과 기술에 대해 설명합니다. 그리고 C#을 통한 JWT 구현 방법도 제공하고 있습니다.

<br>

## 내용
- [JSON 웹 토큰](#url-safe)
- [URL-Safe](#url-safe)
- [JWT 구조](#jwt-구조)
- [JWT 생성 (Generate)](#jwt-생성)
- [JWT 체크 (Validation)](#jwt-validation-체크)

<br>

## JSON 웹 토큰 (Json Web Token, JWT)

| ![image](https://user-images.githubusercontent.com/52397976/144888529-fbe149fa-9af7-4f98-96bc-246fd3b04d76.png) |
|:---:|
| JSON 웹 토큰 |
| (Json Web Token, JWT) |
| Header, Payload, Signiture | 

<br>

## URL-Safe
TBD...

<br>

## JWT 구조
JWT는 3개의 구조로 이루어져 있는 Base64 형태의 암호화된 인증 체계 값입니다.

| Header | Payload | Signiture |
|:---:|:---:|:---:|
| 헤더 | 페이로드 | 시그니쳐 | 

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

<br>

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

<br>

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

<br>

## 참고 문헌
- [OAuth2와 JWT, 웹기반 SSO 인증](https://www.sauru.so/blog/basic-of-oauth2-and-jwt/)
- [.NET 5.0 - Create and Validate JWT Tokens + Use Custom JWT Middleware](https://jasonwatmore.com/post/2021/06/02/net-5-create-and-validate-jwt-tokens-use-custom-jwt-middleware)
- [Create And Validate JWT Token In .NET 5.0
](https://www.c-sharpcorner.com/article/jwt-validation-and-authorization-in-net-5-0/)
- [ASP.NET Core 3.1 - JWT Authentication Tutorial with Example API](https://jasonwatmore.com/post/2019/10/11/aspnet-core-3-jwt-authentication-tutorial-with-example-api)
