## setupProxy
```
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
