## SignalR with React

| Signal R |
|: ---- :|
| ![image](https://user-images.githubusercontent.com/52397976/147094008-a64921bb-6de6-4770-a6ef-0ea28de6e87c.png) |
| Microsoft |
| AspNetCore |



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
