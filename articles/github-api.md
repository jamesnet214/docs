## GitHub API 활용하기

이 리포지토리는 공식 GitHub에서 제공하는 API 활용 방법에 대한 내용을 설명하는 레포지터리입니다.

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

## 내용
- [주요 API 항목](#주요-api-항목)

## 주요 API 항목
DevNcore.org에서 사용중인 GitHub API 목록입니다.

|    | 타입 | 주소 | 설명 |
|:--:|:---:|:----|:----|
| 1 | GET | /login/oauth/authorize | Code 반환 |
| 2 | POST | /login/oauth/access_token | Access 토큰 반환 |

### GitHub API 토큰

#### GitHub OAuth 필요정보

- Client ID
- Client secrets

#### 토큰 발급 방법(사진 첨부 예정)
1. 우측 상단 프로필에서 **Settings** 클릭
2. 좌측 하단 **Developer settings** 클릭
3. **Personal access tokens** 클릭
4. 우측 상단 **Generate new token** 클릭
5. **Note** 토큰의 이름을 입력하고 **Select scopes** 허가할 권한을 체크후 하단 **Generate token**을 클릭한다.
6. 토큰 생성 **(토큰은 최초 한번만 보여지므로 복사 후 안전한 곳에 저장)**

>토큰을 발급 받지 않으면 시간당 60회 호출 제한이 있다(토큰 발급 후 시간당 5000회)

