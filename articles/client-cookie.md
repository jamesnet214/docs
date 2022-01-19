## 클라이언트 Cookie

이 리포지토리는 클라이언트 Cookie에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### 쿠키란(Cookie)?
하이퍼 텍스트의 기록서(HTTP)의 일종으로서 인터넷 사용자가 어떠한 웹사이트를 방문할 경우 그 사이트가 사용하고 있는 서버를 통해 인터넷 사용자의 컴퓨터에 설치되는 작은 기록 정보 파일을 말합니다.
이 기록 파일에 담긴 정보는 인터넷 사용자가 같은 웹사이트를 방문할 때마다 읽히고 수시로 새로운 정보로 바뀝니다.

### 쿠키의 활용
로컬에 있는 쿠키 값을 이용하여 서버에 부담을 줄이고 JWT 토큰을 이용하여 사용자의 ID 정보를 간단하고 빠르게 가져와 사용 할 수 있다.

### 쿠키 사용방법
자세한 쿠키사용 방법은 [여기](https://www.npmjs.com/package/universal-cookie)를 참고해주세요.
쿠키 모듈설치 및 사용코드

> npm install universal-cookie

```react
import Cookies from 'universal-cookie';

const cookies = new Cookies();

const cookies = new Cookies();
    const token = cookies.get('portal.authentication.session');
``` 
