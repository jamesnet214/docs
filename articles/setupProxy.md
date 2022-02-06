## SetupProxy
  
이 리포지토리는 setupProxy 기술을 활용하는데 필요한 설명을 다루는 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
  
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/wpf-code-rules/stargazers"><img src="https://img.shields.io/github/stars/devncore/wpf-code-rules" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/wpf-code-rules" alt="License"> | <a href="https://github.com/devncore/wpf-code-rules/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/wpf-code-rules" alt="Commits-per-month"></a> |

<br />

### setupProxy
```jsx
const { createProxyMiddleware } = require("http-proxy-middleware");

module.exports = function(app) { 
    app.use( ["/api"], 
        createProxyMiddleware({ 
            target: "https://localhost:7073", 
            changeOrigin: true, 
            secure: false, 
            headers: { 
                "Content-Type": "application/json",
                'Access-Control-Allow-Origin': "*",
                "Access-Control-Allow-Credentials": "*", 
                "Access-Control-Allow-Methods": "*" 
            } }
        ) 
    ); 
    app.listen(4937); 
};
```
