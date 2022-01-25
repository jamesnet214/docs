## PL/SQL

이 리포지토리는 PL/SQL에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

## PL/SQL 이란?
PL/SQL 은 상용 관계형 데이터베이스 시스템인 오라클 DBMS에서 SQL 언어를 확장하기 위해 사용하는 컴퓨터 프로그래밍 언어 중 하나이다.
PL/SQL 은 오라클 데이터베이스 버전7, 타임스텐인메모리 데이터베이스 버전 11.2.1, IBM DB2 버전 9.7 부터 사용 가능하다.

<br />

## PL/SQL 특징
- SQL을 확장한 절차적 언어
- 관계형 데이터베이스에서 사용되는 Oracle의 표준 데이터 엑세스 언어, 프로시저 생성자를 SQL과 완벽하게 통합
- 유저 프로세스가 PL/SQL 블록을 보내고 서버 프로세스에서는 PL/SQL Engine에서 해당 블록을 받고 SQL과 프로시저를 나누어 SQL은 SQL Statement Executer로 보낸다.
- 오라클에서 지원하는 프로그래밍 언어의 특성을 수용, SQL에서는 사용할 수 없는 절차적 프로그래밍 기능을 가진다.
- PL/SQL 프로그램의 종류는 크게 Procedure, Function, Trigger 로 나누어 진다.

<br />

## PL/SQL Block 구조
| 영역 | 설명|
|:---:|:---:|
| DECLARE (선언부) | PL/SQL에서 사용하는 모든 변수나 상수를 선언하는 부분, DECLARE로 시작하며 변수나 상수, 커서등을 선언 |
| BEGIN (실행부) | 절차적 형식으로 SQL문을 실행할 수 있도록 절차적 언어의 요소인 제어문, 반복문, 함수 정의 등 로직을 기술할 수 있는 부분, BEGIN으로 시작 |
| EXCEPTION (예외처리부) | PL/SQL 문이 실행중에 에러가 발생하는 경우 예외사항이라하고 이를 해결하기 위한 문장을 기술하는 부분 |
| END (실행문 종료) | PL/SLQ문 종료선언|

<br />

## PL/SQL 자료형
PL/SQL의 주요 자료형은 NUMBER, CHAR, VARCHAR2, DATE, TIMESTAMP 등이 있습니다.

- 수치 변수
```SQL
variable_name number([P, S]) := 0;
```

- 문자 변수
```SQL
variable_name varchar2(20) := 'Text';
```

- 날짜 변수
```SQL
variable_name date := to_date('01-01-2005 14:20:23', 'DD-MM-YYYY hh24:mi:ss');
```

- 예외
코드 실행 중의 오류인 예외는 두 종류가 있습니다. 사용자 정의 예외, 미리 정의된 예외
```SQL
RAISE <exception name>;
```

- 조건문
코드 부분은 IF-THEN-ELSIF 구조로 되어 있습니다.

```SQL
IF x = 1 THEN
   sequence_of_statements_1;
ELSIF x = 2 THEN
   sequence_of_statements_2;
ELSE
   sequence_of_statements_3;
END IF;
```

<br />

## 변수선언
블록내 변수 사용시 DECLARE 선언부에서 변수선언, 변수명 뒤에는 데이터 타입을 기술

- 기본문법
dentifier [CONSTANT] datatype [NOT NULL] [:=[DEFAULT expression];


