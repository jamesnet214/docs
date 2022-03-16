## 문자열 DateTime 변환

이 리포지토리는 문자열을 DateTime으로 변환하는 방법에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### String 문자열을 DateTime 형태로 변환

- Convert.ToDateTime()

```csharp
string stringDate = "2022-03-16";
DateTime dateTime = Convert.ToDateTime(stringDate);
Console.WriteLine(dateTime);

결과 = 2022-03-16 오전 12:00:00
```

```csharp
string stringDate = "2022-03-16 21:15:06";
DateTime dateTime = Convert.ToDateTime(stringDate);
Console.WriteLine(dateTime);

결과 = 2022-03-16 오후 9:15:06
```

```csharp
string stringDate = "2022년03월16일 오후9:15:06";
DateTime dateTime = Convert.ToDateTime(stringDate);
Console.WriteLine(dateTime);

결과 = 2022-03-16 오후 9:15:06
```

- DateTime.Parse()

```csharp
string stringDate = "2022-03-16 22:12:15";
DateTime dateTime = DateTime.Parse(stringDate);
Console.WriteLine(dateTime);

결과 = 2022-03-16 오후 10:12:15
```

```csharp
string stringDate = "2022년03월16일 오후 2시12분15초";
DateTime dateTime = DateTime.Parse(stringDate);
Console.WriteLine(dateTime);

결과 = 2022-03-16 오후 2:12:15
```

- DateTime ParseExact (string s, string format, IFormatProvider? provider) <br />
`s = 변환할 날짜 및 시간이 포함된 문자열` <br />
`format = 날짜 형식을 정의` <br />
`provider = 문화권별 서식 지정 정보를 제공` <br />



```csharp
string stringDate = "20220316";
DateTime dateTime = DateTime.ParseExact(stringDate, "yyyyMMdd", null);
Console.WriteLine(dateTime);

결과 = 2022-03-16 오전 12:00:00
```

```csharp
string stringDate = "2022-03-16 22:02:22";
DateTime dateTime = DateTime.ParseExact(stringDate, "yyyy-MM-dd HH:mm:ss", null);
Console.WriteLine(dateTime); 

결과 = 2022-03-16 오후 10:02:22
```

```csharp
string stringDate = "2022-03-16 12:02:22";
DateTime dateTime = DateTime.ParseExact(stringDate, "yyyy-MM-dd hh:mm:ss", null);
Console.WriteLine(dateTime);

결과 = 2022-03-16 오전 12:02:22
```

```csharp
string stringDate = "2022년03월16일 12시02분22초";
DateTime dateTime = DateTime.ParseExact(stringDate, "yyyy년MM월dd일 HH시mm분ss초", null);
Console.WriteLine(dateTime);

결과 = 2022-03-16 오후 12:02:22
```

```csharp
string stringDate = "20220316220213";
DateTime dateTime = DateTime.ParseExact(stringDate, "yyyyMMddHHmm", null);
Console.WriteLine(dateTime);

결과 = 2022-03-16 오후 10:02:13
```

```csharp
using System.Globalization;
CultureInfo us = new CultureInfo("en-US");
CultureInfo sa = new CultureInfo("ar-SA");
string text = "1443-08-13T22:02";
string format = "yyyy'-'MM'-'dd'T'HH':'mm";
Console.WriteLine(DateTime.ParseExact(text, format, us));
Console.WriteLine(DateTime.ParseExact(text, format, sa));

결과 = 1443-08-13 오후 10:02:00
결과 = 2022-03-16 오후 10:02:00
```



