# SSMS ( SQL Server Management Studio )

## Contents
- 테이블 디자인 변경 옵션 설정

### 테이블 디자인 변경 오류 및 설정방법

MSSQL SSMS 를 사용하다보면 테이블 컬럼 정보 변경시 오류가 발생하는 경우가 있습니다.

| 디자인 변경 오류 |
|:---|
| ![ssms04](https://user-images.githubusercontent.com/76234292/147950884-ea532b10-949b-4953-9e3f-30b8dbb52fd4.PNG) |

> 처음 SSMS 를 설치를 하고 테이블 컬럼 정보 변경시 위의 그림과 같이 오류가 납니다. 
> 기본적으로 테이블 컬럼정보 변경 저장옵션이 막혀 있습니다.
<h6> 도구 -> 옵션</h6>

![ssms01](https://user-images.githubusercontent.com/76234292/147950924-f90b7a63-932a-4772-8a37-5ebea19a32c9.png)

| 변경 전 | 변경 후 |
|:--------:|:------:|
| ![ssms02](https://user-images.githubusercontent.com/76234292/147950931-c30c58fd-4ba3-4cfe-b840-ebdd2fd747c6.PNG) | ![ssms03](https://user-images.githubusercontent.com/76234292/147950952-d3d78d86-00bb-429f-8130-be63c6ce8472.PNG) | 


> 테이블을 다시 만들어야 하는 변경 내용 저장 안함 옵션을 체크 해제 합니다.

이제 테이블 디자이너에서 컬럼 정보를 변경하여 사용이 가능합니다.





