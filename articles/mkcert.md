# 로컬 인증서 발급받기
[DevNcore Team](https://devncore.org)

### 목적
본문은 **[mkcert](https://github.com/FiloSottile/mkcert)** 를 통한 로컬 인증서 발급 방법을 설명합니다. 
> 아주 간단하게, 빠르고 편리하게 localhost SSL 인증서를 발급받을 수 있습니다.

### 지원 운영체제
모든 운영체제에서 사용이 가능합니다.
| Linux | MacOSX | Windows |
|:-----:|:-----:|:-----:|
|<img src="https://user-images.githubusercontent.com/52397976/145034010-450f76a4-a8ad-470c-9c74-2373e925f323.png" width="200"/>|<img src="https://user-images.githubusercontent.com/52397976/145033016-235195ba-d75a-489e-9479-bb25278062c7.png" width="200"/>|<img src="https://user-images.githubusercontent.com/52397976/145033110-c2600e0b-f194-47e5-8940-02ff31691c8e.png" width="200"/>|
| sudo | homebrew | chocolatey |

### Windows OS
Windows 운영체제인 경우 Chocolatey 패키지 관리자를 먼저 설치합니다.
> Windows 소프트웨어용 시스템 수준의 명령줄 패키지 관리자 및 설치 프로그램 입니다.

<img src="https://user-images.githubusercontent.com/52397976/145036063-6f6f83c2-a1b2-41fb-bfe4-d9383697b6a2.png" width="600"/>

- #### PowerShell (관리자 모드) 
  관리자 모드에서 아래 소스코드를 실행합니다.  
  
  ```
  Set-ExecutionPolicy Bypass -Scope Process -Force; 
  [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; 
  iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
  ```
  > 공식 [홈페이지](https://chocolatey.org/install)에서도 설치 주소를 확인할 수 있습니다.
  
  설치가 잘 되었는지 확인하는 방법은 다음과 같습니다.
  ```
  choco -v
  ```
  
  [mkcert](https://github.com/FiloSottile/mkcert) 패키지 설치
  ```
  choco install mkcert
  ```
  > 알고 계셨나요? [mkcert](https://github.com/FiloSottile/mkcert)은 무료 오픈소스입니다.

## 인증서 발급하기
이제 원하는 위치에서 SSL 인증서를 생성할 수 있습니다. 
> mkcert 기능은 cmd, terminal, node 등의 콘솔 사용이 가능합니다.
<img src="https://user-images.githubusercontent.com/52397976/145218140-170cee55-bdc2-40ee-a252-4e21ccb1a488.png" width="400"/>

- #### 콘솔 애플리케이션 (관리자 모드)

  1. 로컬 환경에서 신뢰할 수 있는 CA 생성   
  
  ```
  mkcert -install
  ```

  2. SSL 인증서 생성
  3. 
  ```
  mkcert localhost
  ```

<img src="https://user-images.githubusercontent.com/52397976/145216640-5d8beb54-14a1-489e-a34d-338488a03f8e.png" width="400"/>


## 참고자료
- [How to configure https (SSL) locally?](https://www.mariokandut.com/how-to-setup-https-ssl-in-localhost-react/)
