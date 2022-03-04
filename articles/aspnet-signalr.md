## Contents
- [ASP.NET SignalR](#aspnet-signalr)
- [SignalR 전송 방식](#signalr-전송-방식)
- [SignalR 통신 방법](#signalr-통신-방법)
- 예제1 (모의 주식 시세 앱)
- [예제2 (실시간 채팅 앱)](#예제2-실시간-채팅-앱)

<br/>

## ASP.NET SignalR
**ASP.NET SignalR**은 앱에 실시간 웹 기능을 추가하는 것을 간소화하는 오픈소스 라이브러리입니다. 실시간 웹 기능을 사용하면 서버측 코드에서 클라이언트에 콘텐츠를 즉시 푸시할 수 있습니다.

#### ✔️ SignalR 사용이 적합한 앱
- 서버에서 자주 업데이트 해야 하는 앱. (게임, 소셜 네트워크, 투표, 경매, 지도 및 GPS 등)
- 대시보드 및 모니터링 앱.
- 공동 작업 앱. (화이트보드 앱, 팀 회의 소프트웨어)
- 알림이 필요한 앱. (소셜 네트워크, 이메일, 채팅 등)

#### ✔️ SignalR의 기능
- 연결 관리를 자동으로 처리함
- 모든 연결된 클라이언트에 동시에 메시지 전송
- 특정 클라이언트/클라이언트 그룹으로 메시지 전송
- 늘어난 트래픽을 처리하도록 크기 조정

<br/>

## SignalR 전송 방식
SignalR은 세 가지 전송 방식이 있으며, 서버와 클라이언트 성능에 따른 범위 안에서 최선의 전송방식을 자동으로 선택합니다.

<img src="https://user-images.githubusercontent.com/74305823/156685043-2409d707-b71c-4a3f-8bf3-dbe4f9ad9888.png" width="400"/>

### 1. WebSocket

<img src="https://user-images.githubusercontent.com/74305823/156685249-c5db8cdc-f2f1-4bdb-91b2-61706978375e.png" width="400"/>

**WebSocket**은 사용자의 브라우저와 서버 사이의 인터랙티브 통신 세션을 설정할 수 있게 하는 고급 기술입니다. 개발자는 웹 소켓 API를 통해 서버로 메시지를 보내고 서버의 응답을 받기 위해 서버를 폴링하지 않고도 이벤트 중심 응답을 받을 수 있습니다.

### 2. Server-Sent Events

<img src="https://user-images.githubusercontent.com/74305823/156686190-8d7f010a-eae6-4c23-93db-fb948813c731.png" width="460"/>

전통적으로 웹 페이지는 새로운 데이터를 받기 위해 서버로 요청을 보내야 하지만, **Server-Sent Events** 방식은 요청 없이도 언제든지 서버가 새로운 데이터를 보낼 수 있습니다. 이렇게 보내진 메시지는 웹 페이지 안에서 Events와 데이터로 다룰 수 있습니다.

### 3. Long Polling

<img src="https://user-images.githubusercontent.com/74305823/156686648-c98b1ba1-d498-4745-87d0-09567e9f5523.png" width="400"/>

**Long Polling** 방식은 서버에 요청을 보내고 서버 이벤트가 발생할 때까지 연결을 유지합니다. 이때 이벤트가 발생하면 응답을 받아 처리하고, 즉시 또 다른 이벤트를 받기 위해 연결을 맺습니다.

<br/>

## SignalR 통신 방법

<img src="https://user-images.githubusercontent.com/74305823/156687666-819cc830-0c1d-4d07-92dd-0ab7f0683bd8.png" width="600"/>

SignalR은 Server에선 Hub, Client에선 Hub Proxy로 연결되어 서로 통신합니다. Server의 Hub는 서버코드에서 클라이언트에 의해 호출되는 메서드나 연결된 클라이언트의 메서드를 호출하는 메서드를 정의합니다.

<br/>

## 예제1 (모의 주식 시세 앱)

<br/>

## 예제2 (실시간 채팅 앱)
> Visual Studio 2019로 구현하였습니다.

### 1. 새 프로젝트 만들기

![image](https://user-images.githubusercontent.com/74305823/156701747-bb3a53fc-49d5-4d82-8be0-0f357cced94b.png)  
![image](https://user-images.githubusercontent.com/74305823/156702015-5cfbab9c-cd45-4c19-a90c-f10c3b705121.png)  
![image](https://user-images.githubusercontent.com/74305823/156702043-555a284f-bbde-422f-a88a-b844df8a04b5.png)
![image](https://user-images.githubusercontent.com/74305823/156702090-d5967934-ecca-4d55-b11e-dc91735fd1d5.png)

<br/>

### 2. SignalR 패키지 추가

- wwwroot → 추가 → 클라이언트 쪽 라이브러리

![image](https://user-images.githubusercontent.com/74305823/156702492-4821bb5b-8598-4ebf-a09b-888cca12ea20.png)

- **'@microsoft/signalr'** 라이브러리 선택 후 `특정 파일 선택`에서 `파일 수 > dist > browser` 디렉터리의 **`signalr.js`**, **`signalr.min.js`** 파일을 선택하여 설치합니다.

![image](https://user-images.githubusercontent.com/74305823/156703136-5f13d8be-cadb-407c-90fb-950c1080b958.png)

- 설치가 완료되면 `wwwroot` 디렉터리 하위에 `microsoft` 폴더가 생긴 것을 확인할 수 있습니다.

![image](https://user-images.githubusercontent.com/74305823/156703478-1e2ea3d3-8fe7-4b40-af76-776c0fdbf989.png)

<br/>

### 3. SignalR Hub 구성 및 Method 생성

- 솔루션에 'Hubs' 폴더 생성 후 `ChattingHub.cs` 파일을 추가합니다.  

![image](https://user-images.githubusercontent.com/74305823/156704427-784c01ad-56d7-4e14-bb01-a0f8d2de6f2a.png)

- ChattingHub 클래스에 Method를 생성합니다. ChattingHub 클래스는 Hub 클래스를 상속받습니다.
```csharp
using Microsoft.AspNetCore.SignalR;
using System.Threading.Tasks;

namespace ChattingApp.Hubs
{
    public class ChattingHub : Hub
    {
        [HubMethodName("Send")]
        public async Task SendMessage(string id, string message)
        {
            await Clients.All.SendAsync("Received", id, message);
        }
    }
}
```

<br/>

### 4. `Startup.cs` 수정

- `ConfigureServices` 메서드에 SignalR을 설정합니다.
```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllersWithViews();
    services.AddSignalR();  // SignalR 설정
}
```

- `Configure` 메서드의 endpoint에 SignalR 경로를 설정합니다.

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
    endpoints.MapHub<ChattingHub>("/hubs");  // SignalR 경로 설정
});
```

<br/>

### 5. Client SignalR 설정
- `Views > Home` 디렉터리의 `index.cshtml`파일을 아래와 같이 수정합니다.

```javascript
@{
    ViewData["Title"] = "Home Page";
}

<div class="text-center" style="margin-top: 10px; margin-left: 30px;">
    ID : <input type="text" id="id" />
</div>
<div class="text-center" style="margin-top: 10px; margin-left: 13px;">
    내용 : <input type="text" id="message" />
</div>
<div class="text-center" style="margin-top: 10px; margin-left: 13px;">
    <button id="submit">전송</button>
</div>
<div class="row">
    <div class="col-12">
        <hr />
    </div>
</div>
<div class="row">
    <div class="col-6">
        <ul id="messageList"></ul>
    </div>
</div>

<script src="~/lib/jquery/dist/jquery.js"></script>
<script src="~/microsoft/signalr/dist/browser/signalr.js"></script>

<script type="text/javascript">
    $(function () {
        var connection = new signalR.HubConnectionBuilder().withUrl("/hubs").build();  // SignalR 허브 연결

        // Server Method 호출
        connection.start().then(function () {
            $("#submit").click(function () {
                connection.invoke("Send", $("#id").val(), $("#message").val());
            });
        });

        // Server단에서 Client Method 호출
        connection.on("Received", function (user, message) {
            var msg = message.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;");
            var encodeMsg = user + " : " + msg;
            var li = document.createElement("li");
            li.textContent = encodeMsg;
            document.getElementById("messageList").appendChild(li);
        });
    });
</script>
```

<br/>

### 6. 실행 후 테스트
![image](https://user-images.githubusercontent.com/74305823/156705754-2897aa00-9220-44aa-af2f-229181167cee.png)

<br/>

## References
- https://www.codemag.com/article/1807061/Build-Real-time-Applications-with-ASP.NET-Core-SignalR
- http://www.egocube.pe.kr/translation/content/asp-net-signalr/201401150001
- https://dev.to/emrekas/what-is-signalr-core-how-does-it-work-49f5
