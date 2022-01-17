## Rest API
이 리포지토리는 Rest API의 기본적인 사용법에 대해 기술한 리포지토리입니다. <br />
  
<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>

| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/the-easiest-git/stargazers"><img src="https://img.shields.io/github/stars/devncore/the-easiest-git" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/the-easiest-git" alt="License"> | <a href="https://github.com/devncore/the-easiest-git/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/the-easiest-git" alt="Commits-per-month"></a> |

<br />

### RESTful API 구성요소

#### Resource
서버는 유니크한 ID를 가진 `Resource` 가 있으며 클라이언트는 `Resource`에 요청을 보내고 이러한 `Resource` 를 URI 라고 합니다.
 
#### Method
서버에 요청을 보내기 위한 방식으로 GET, POST, PUT, PATCH, DELETE가 있으며 CRUD 처리를 위해 연산에 맞는 Method를 사용하여 서버에 요청을 보냅니다.

#### Representation of Resource
클라이언트와 서버가 데이터를 주고받는 형태로는 json, xml, text, rss 등이 있으며 주로 Key, Value를 활용하는 json을 사용합니다.

<br />

### REST 특징
- 일관된 인터페이스 (Uniform Interface)
Uniform Interface란, Resource(URI)에 대한 요청을 통일되고, 한정적으로 수행하는 아키텍처 스타일을 의미합니다. 이것은 요청을 하는 Client가 플랫폼(Android, Ios, Jsp 등) 에 무관하며, 특정 언어나 기술에 종속받지 않는 특징을 의미합니다. 이러한 특징 덕분에 Rest API는 HTTP를 사용하는 모든 플랫폼에서 요청가능하며, Loosely Coupling(느슨한 결함) 형태를 갖게 되었습니다.
 
- 무상태성 (Stateless)
서버는 각각의 요청을 별개의 것으로 인식하고 처리해야하며, 이전 요청이 다음 요청에 연관되어서는 안됩니다. 그래서 Rest API는 세션정보나 쿠키정보를 활용하여 작업을 위한 상태정보를 저장 및 관리하지 않습니다. 이러한 무상태성때문에 Rest API는 서비스의 자유도가 높으며, 서버에서 불필요한 정보를 관리하지 않으므로 구현이 단순합니다. 이러한 무상태성은 서버의 처리방식에 일관성을 부여하고, 서버의 부담을 줄이기 위함입니다.

- 캐시 가능 (Cacheable)
Rest API는 결국 HTTP라는 기존의 웹표준을 그대로 사용하기 때문에, 웹의 기존 인프라를 그대로 활용할 수 있습니다. 그러므로 Rest API에서도 캐싱 기능을 적용할 수 있는데, HTTP 프로토콜 표준에서 사용하는 Last-Modified Tag 또는 E-Tag를 이용하여 캐싱을 구현할 수 있고, 이것은 대량의 요청을 효울척으로 처리할 수 있게 도와줍니다.

- 서버-클라이언트 구조 (Client-Server Architecture)
Rest API에서 자원을 가지고 있는 쪽이 서버, 자원을 요청하는 쪽이 클라이언트에 해당합니다. 서버는 API를 제공하며, 클라이언트는 사용자 인증, Context(세션, 로그인 정보) 등을 직접 관리하는 등 역할을 확실히 구분시킴으로써 서로 간의 의존성을 줄입니다.
 

- 자체 표현 (Self-Descriptiveness)
Rest API는 요청 메세지만 보고도 이를 쉽게 이해할 수 있는 자체 표현 구조로 되어있습니다. 아래와 같은 JSON 형태의 Rest 메세지는 http://localhost:8080/board 로 게시글의 제목, 내용을 전달하고 있음을 손쉽게 이해할 수 있습니다. 또한 board라는 데이터를 추가(POST)하는 요청임을 파악할 수 있습니다.
 

- 자체 표현 (Layered System)
Rest API의 서버는 다중 계층으로 구성될 수 있으며 보안, 로드 밸런싱, 암호화 등을 위한 계층을 추가하여 구조를 변경할 수 있습니다. 또한 Proxy, Gateway와 같은 네트워크 기반의 중간매체를 사용할 수 있게 해줍니다. 하지만 클라이언트는 서버와 직접 통신하는지, 중간 서버와 통신하는지 알 수 없습니다.

<br />

### REST 규칙
- URI는 명사를 사용한다.
- 슬래시로 계층 관계를 표현한다.
- URI의 마지막에는 슬래시를 붙이지 않는다.
- URI는 소문자로만 구성한다.
- 가독성이 떨어지는 경우 하이픈을 사용한다.

