## SignalR with React

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
