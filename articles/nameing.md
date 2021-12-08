# 네이밍 표기법

네이밍과 표기법에 관한 정보

## Overview
- [파스칼 표기법](#파스칼-표기법)
- [카멜 표기법](#카멜-표기법)
- [클래스명 표기법]
- [함수명(Method) 표기법]
- [변수명, 함수 파라미터]
- [인터페이스명]
- [변수명](#Boolean)

## 파스칼 표기법
> 파스칼 표기법이란? </br>
> 파스칼 기법은 모든 단어에서 첫번째 문자는 대문자로 시작하며 나머지는 소문자이다. </br>
```
DataModel
```

## 카멜 표기법
> 카멜 표기법이란? </br>
> 첫번째 단어의 문자만 소문자로 시작하고 다음 단어부터 첫글자는 대문자로 시작한다. </br>
> 나머지는 모두 소문자로 사용한다.
```
dataModel
```

## class명
> 파스칼 표기법
```
public class DataModel
{
}
```

## 함수(Method)명
> 파스칼 표기법
```
void GetData(string name)
{
}
```

## 변수 및 함수 파라미터명
> 카멜 표기법 </br>
> 변수명에는 헝가리안 표기법을 사용하지 않는다. </br>
> 변수명에 약어를 사용하지 않는다. </br>
> 변수명에 한 글자로 된 i, n, s... 같은 이름을 사용하지 않는다. (for문 제외)
```
int totalCount = 0;
void GetData(string name)
{
    string myName = name;
}
```

## 인터페이스명
> 파스칼 표기법, 접두사 I 를 포함하여 파스칼 표기법을 사용
```
public interface IMyName
{
}
```

## 지역변수와 멤버변수
> 카멜 표기법
> 멤버변수에는 변수명 앞에 _ 밑줄을 사용한다. </br>
> 지역변수에는 변수명 앞에  밑줄을 사용하지 않는다.
```
public class DataModel
{
    string _name;
    int _age;
    public void GetData()
    {
        int day = 0;
        string address = "";
    }
}
```

## Boolean 변수,속성,함수
> is 또는 유사한 접두사를 사용한다.



- ### `UI 구성요소 접두사 적용`
| Control | Prefix | Control | Prefix | Control | Prefix |
|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
| Label | lbl | ListBox | lst | Image | img |
| TextBox | txt | DataList | dtl | Panel | pnl |
| DataGrid | dtg | Repeater | rep | PlaceHolder | phd |
| Button | btn | CheckBox | chk | Table | tbl |
| ImageButton | imb | CheckBoxList | cbl | Validators | val |
| Hyperlink | hlk | RadioButton | rdo | DropDownList | ddl |
| RadioButtonList | rbl |
