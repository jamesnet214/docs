## WPF Circle 그리기
이 리포지토리는 WPF에서 삼각함수를 사용해 x, y 좌표를 구한 후 원을 그리는 방법을 설명하는 Article입니다.

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
  
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

## 삼각함수 공식

| 참고 이미지 |
|:-----:|
| <img src="https://user-images.githubusercontent.com/68521148/145054110-4aaf0d61-41d9-4711-ae24-b535efa27ebb.png"></img> |

**@ = 각도, r = 반지름, a = 높이, b = 밑변**

```
Sin@: a / r => a(y좌표): Sin@ * r
Cos@: b / r => b(x좌표): Con@ * r
```

위 공식에서 Sin, Cos 와 a, b 위치를 바꾸어 x, y 좌표를 구한 후    
원은 360도. 원을 그리려면 0도와 360도 지점 좌표를 구해 Shape로 그려주면 되는데
세타(디그리) 값을 라디안으로 변환해 넣어줘야 합니다.

**Math.PI = 3.14159265...** 

```
startAngle = 0도 * Math.PI / 180
endAngle = 360도 * Math.PI / 180
```

최종 C# 코드

```C#
//0도 지점 x, y 좌표
double x1 = Math.Sin(startRadian) * r;
double y2 = Math.Cos(startRadian) * r;

//360도 지점 x, y 좌표
double x2 = Math.Sin(endRadian) * r;
double y2 = Math.Cos(endRadian) * r;
```

<img src="https://user-images.githubusercontent.com/68521148/145227901-0dd26880-6cc0-4005-921d-bf6d1e929e41.png" width="400" height="400"></img>

위에서 이어질 두개의 포인트 좌표, 시작 각도, 끝 각도를 구했고 그려질 원의 지름을 임의로 정해줍니다.

<br />
