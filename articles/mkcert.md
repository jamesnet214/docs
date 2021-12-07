# 로컬 인증서 발급받기
[DevNcore Team](https://devncore.org)

### 목적
본문은 **MkCert** API를 통한 로컬 인증서 발급 방법을 설명합니다. 
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
  설치 완료 후 확인하기.
  ```
  choco -v
  ```

## Install

- Step 1. Install: Chocoletley
- Step 2. Install: `choco install mkcert`
- Step 3. Install: `install mkcert`
- Step 4. Install: `mkcert localhost`
