## Contents
- [ASP.NET SignalR](#aspnet-signalr)
- [SignalR Transport Methods](#signalr-transport-methods)
- 예제1 (모의 주식 시세 앱)
- 예제2 (실시간 채팅 앱)

<br/>

## ASP.NET SignalR
**ASP.NET Core SignalR**은 앱에 실시간 웹 기능을 추가하는 것을 간소화하는 오픈소스 라이브러리입니다. 실시간 웹 기능을 사용하면 서버측 코드에서 클라이언트에 콘텐츠를 즉시 푸시할 수 있습니다.

#### SignalR 사용이 적합한 앱
- 서버에서 자주 업데이트 해야 하는 앱. (게임, 소셜 네트워크, 투표, 경매, 지도 및 GPS 등)
- 대시보드 및 모니터링 앱.
- 공동 작업 앱. (화이트보드 앱, 팀 회의 소프트웨어)
- 알림이 필요한 앱. (소셜 네트워크, 이메일, 채팅 등)

#### SignalR의 기능
- 연결 관리를 자동으로 처리함
- 모든 연결된 클라이언트에 동시에 메시지 전송
- 특정 클라이언트/클라이언트 그룹으로 메시지 전송
- 늘어난 트래픽을 처리하도록 크기 조정

<br/>

## SignalR Transport Methods
SignalR은 세 가지 전송 타입이 있습니다.  

<img src="https://user-images.githubusercontent.com/74305823/156685043-2409d707-b71c-4a3f-8bf3-dbe4f9ad9888.png" width="400"/>


<br/>

## References
- https://www.codemag.com/article/1807061/Build-Real-time-Applications-with-ASP.NET-Core-SignalR
- http://www.egocube.pe.kr/translation/content/asp-net-signalr/201401150001
- https://dev.to/emrekas/what-is-signalr-core-how-does-it-work-49f5
