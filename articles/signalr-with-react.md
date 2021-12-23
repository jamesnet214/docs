## SignalR with React

| Signal R |
|:----:|
| ![image](https://user-images.githubusercontent.com/52397976/147094008-a64921bb-6de6-4770-a6ef-0ea28de6e87c.png) |
| Microsoft |
| .NET Core (또는 과거 .NET Framework) |

> SignalR은 실시간 통신과 Push 기능을 간소화하여 간편하게 사용할 수 있도록 제공해 주는 오픈소스 라이브러리입니다.

SignalR은 AspNetCore를 통해 제공되며 기존 .NET Framework용 버전도 있으나 최신 버전과는 상당히 다르며 AspNetCore 기반의 SignalR을 


** Create Hub**

```
public class ChatHub : Hub
{
    public async Task SendMessage(string user, string message)
    {
        await Clients.All.SendAsync("receiveMessage", user, message);
    }
}
```

**ConfigureServices**

```
services.AddSignalR();
```

**Configure**

```
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<ChatHub>("/chatHub");
}
```

## Create client scripts

****chat.js
    
```
var connection = new signarR.HubConnectionBuilder();
```


TBD...

(이미지 1) - AspNetCore API 프로젝트 선택

(이미지 2) - 프로젝트 이름 AspNetCore

(이미지 3) - 추가정보 확인

(이미지 4) - 프로젝트 솔루션

(이미지 5) Add > Client side library

(이미지 6) 라이브러리 입력 및 특정파일 선택 (.js 추출)

파일 추가
`Hubs/ChatHub.cs`
    
```
using Microsoft.AspNetCore.SignalR;

namespace SignalRCore.Hubs
{
    public class ChatHub : Hub
    {
        public async Task SendMessage(string user, string message)
        {
            // 접속중인 모든 클라이언트에 일괄적으로 메시지를 보낼 수 있습니다.
            await Clients.All.SendAsync("ReceiveMessage", user, message);
        }
    }
}
```

시그널R 서비스 추가
```
public void ConfigureServices(IServiceCollection services)
{
    ...
    services.AddSignalR();
}
```

Endpoints 허브 추가
```
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    ...
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapHub<chatHub>("/chatHub");
        endpoints.MapControllers();
    });
}
```

크로스 도메인을 허용할 때
```
app.UseCors(builder =>
{
    builder.WaitOrigins("https://localhost:4936")
        .AllowAnyHeader()
        .AllowAnyMethod()
        .AllowCredentials();
});
```

 
`chatHub.js`    
```
"use strict";

var connection = new signalR.HubConnectionBuilder().withUrl("/chatHub").build();

//Disable the send button until connection is established.
document.getElementById("sendButton").disabled = true;

connection.on("ReceiveMessage", function (user, message) {
    var li = document.createElement("li");
    document.getElementById("messagesList").appendChild(li);
    // We can assign user-supplied strings to an element's textContent because it
    // is not interpreted as markup. If you're assigning in any other way, you 
    // should be aware of possible script injection concerns.
    li.textContent = `${user} says ${message}`;
});

connection.start().then(function () {
    document.getElementById("sendButton").disabled = false;
}).catch(function (err) {
    return console.error(err.toString());
});

document.getElementById("sendButton").addEventListener("click", function (event) {
    var user = document.getElementById("userInput").value;
    var message = document.getElementById("messageInput").value;
    connection.invoke("SendMessage", user, message).catch(function (err) {
        return console.error(err.toString());
    });
    event.preventDefault();
});
```

`Client source`
```
    <div class="container">
        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-2">User</div>
            <div class="col-4"><input type="text" id="userInput" /></div>
        </div>
        <div class="row">
            <div class="col-2">Message</div>
            <div class="col-4"><input type="text" id="messageInput" /></div>
        </div>
        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-6">
                <input type="button" id="sendButton" value="Send Message" />
            </div>
        </div>
    </div>
    <div class="row">
        <div class="col-12">
            <hr />
        </div>
    </div>
    <div class="row">
        <div class="col-6">
            <ul id="messagesList"></ul>
        </div>
    </div>
<script src="~/js/signalr/dist/browser/signalr.js"></script>
<script src="~/js/chat.js"></script>
```
