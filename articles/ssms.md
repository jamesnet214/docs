# SSMS ( SQL Server Management Studio )

## Contents
- 테이블 디자인 변경 옵션 설정

### 테이블 디자인 변경 오류 및 설정방법

> SSMS 사용중 테이블 컬럼 정보 변경시 오류가 발생하는 경우 입니다.

| 디자인 변경 오류 |
|:---|
| ![111](https://user-images.githubusercontent.com/76234292/148226320-5d1d1528-4cd5-49fb-ac00-57eef6e4ac6e.png) |

<br />

```
기본적으로 테이블 컬럼정보 변경 저장옵션이 체크 되어 있습니다.
옵션을 변경합니다.
```

| 도구 -> 옵션 |
|:--------:|
| ![222](https://user-images.githubusercontent.com/76234292/148228070-83a1b42c-b10d-4474-ac6d-194b86f3ccd1.png) |



<br />

| 변경 전 | 변경 후 |
|:--------:|:------:|
| ![ssms02](https://user-images.githubusercontent.com/76234292/147950931-c30c58fd-4ba3-4cfe-b840-ebdd2fd747c6.PNG) | ![ssms03](https://user-images.githubusercontent.com/76234292/147950952-d3d78d86-00bb-429f-8130-be63c6ce8472.PNG) | 

```
테이블을 다시 만들어야 하는 변경 내용 저장 안함 옵션을 체크 해제 합니다.
이제 테이블 디자이너에서 컬럼 정보를 변경하여 사용이 가능합니다.
```
