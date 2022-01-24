## Database Schema

이 리포지토리는 Database Schema에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### Database Schema 란?
데이터베이스 스키마(database schema)는 데이터베이스에서 자료의 구조, 자료의 표현 방법, 자료 간의 관계를 형식 언어로 정의한 구조입니다.
데이터베이스 관리 시스템(DBMS)이 주어진 설정에 따라 데이터베이스 스키마를 생성하며, 데이터베이스 사용자가 자료를 저장, 조회, 삭제, 변경할 때 DBMS는 자신이 생성한 데이터베이스 스키마를 참조하여 명령을 수행합니다.
데이터베이스의 구조와 제약조건에 관해 전반적인 명세를 기술한 것을 말합니다.

<br />

### 스키마 구조

| 스키마| 설명 |
|:-----:|:----:|
| 외부 스키마(External Schema)   | 프로그래머나 사용자의 입장에서 데이터베이스의 모습으로 조직의 일부분을 정의한 것 |
| 개념 스키마(Conceptual Schema) | 모든 응용 시스템과 사용자들이 필요로하는 데이터를 통합한 조직 전체의 데이터베이스 구조를 논리적으로 정의한 것 |
| 내부 스키마(Internal Schema)   | 전체 데이터베이스의 물리적 저장 형태를 기술하는 것 |

<br />

### 스키마 특징

- 데이터베이스 개체에 대한 네임스페이스
- 스키마의 기본값은 dbo
- DB에 존재하는 스키마 정보 조회, 해당하는 테이블의 스키마 조회 가능
- 스키마를 생성하고 생성한 스키마를 UserId에 맵핑하여 사용
- 유저에 스키마가 맵핑 되었다면 테이블, 프로시저 생성시 기본적으로 맵핑된 스키마로 생성됨
