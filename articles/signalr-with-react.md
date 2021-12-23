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
