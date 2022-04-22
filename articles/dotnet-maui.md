# MAUI (Multi-platform App UI)

이 리포지토리는 MAUI 에 대하여 설명합니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br>

## MAUI란?

.NET MAUI는 C#과 XAML을 사용하여 네이티브 모바일 및 데스크톱 앱을 만들기 위한 플랫폼 간 프레임워크입니다.

.NET MAUI는 Xamarin.Forms의 다음 단계로 볼 수 있는데, 가장 큰 차이점은 아래와 같습니다.

- 모든 플랫폼을 단일 프로젝트에서 관리 가능
- 한 곳에서 모든 자산 관리
- 플랫폼별 코드를 구성하기 위한 멀티 타겟팅
- MVU(Model View Update) 패턴에 대한 기본 지원
- Blazor 지원

<br>

![image](https://user-images.githubusercontent.com/74305823/158945628-e1cadebc-84aa-48dc-bf3f-39b15ee2588f.png)

## MAUI 단일 프로젝트
MAUI 앱은 일반적으로 Android, iOS, macOS 및 Windows 대상으로 지정할 수 있는 단일 프로젝트로 구성되며, 아래와 같은 이점이 있습니다.
- 여러 플랫폼 및 디바이스를 대상으로 하는 하나의 프로젝트.
- 한 곳에서 글꼴 및 이미지와 같은 리소스를 관리.
- 플랫폼별 코드를 구성하는 멀티 타겟팅.

<img src="https://user-images.githubusercontent.com/74305823/160987500-9e6615fe-0504-4250-992f-fe66b14d92b3.png" width="350"/>

### 리소스 파일
각 플랫폼마다 리소스를 관리하는 고유한 접근방식이 있기 때문에 크로스플랫폼 앱 개발에서 리소스를 관리하는 것은 일반적으로 문제가 있었습니다. 하나의 이미지는 각 플랫폼에 맞게 여러 번 복제되었으며, 이로 인해 각 플랫폼에서 서로 다른 파일 이름 또는 폴더 규칙을 사용해야 했습니다.

MAUI 단일 프로젝트를 사용하면 리소스 파일을 한 곳에 저장하여 각 플랫폼에서 사용할 수 있습니다. 리소스 파일에는 앱 아이콘, 글꼴, 이미지, 시작 화면 등이 포함됩니다.

<table>
<th>리소스</th>
<th>빌드 작업</th>
<th>추가 예시</th>
<tr>
  <td>앱 아이콘</td>
  <td>MauiIcon</td>
  <td>
    
  ```xml
    <MauiIcon Include="Resources\Images\appicon.png" />
  ```
  </td>
</tr>
<tr>
  <td>글꼴</td>
  <td>MauiFont</td>
  <td>
    
  ```xml
    <MauiFont Include="Resources\Fonts\OpenSans-Regular.ttf" />
  ```
  </td>
</tr>
<tr>
  <td>이미지</td>
  <td>MauiImage</td>
  <td>
    
  ```xml
    <MauiImage Include="Resources\Images\logo.jpg" />
  ```
  </td>
</tr>
<tr>
  <td>시작화면</td>
  <td>MauiSplashScreen</td>
  <td>
    
  ```xml
    <MauiSplashScreen Include="Resources\Images\splashscreen.svg" />
  ```
  </td>
</tr>
<tr>
  <td>원시자산</td>
  <td>MauiAsset</td>
  <td>
    
  ```xml
    <MauiAsset Include="Resources\Raw\index.html" />
  ```
  </td>
</tr>
<tr>
  <td>CSS 파일</td>
  <td>MauiCss</td>
  <td>
    
  ```xaml
    <Application ...>
        <Application.Resources>
            <StyleSheet Source="/Resources/styles.css" />
        </Application.Resources>
    </Application>
  ```
  </td>
</tr>
</table>

<br>

## Reference
- https://docs.microsoft.com/ko-kr/dotnet/maui/what-is-maui
- https://dev.grapecity.co.kr/bbs/board.php?bo_table=component_bntips&wr_id=86

<br/>
