# WPF 원그리기

삼각함수를 사용해 x, y 좌표를 구한 후 원을 그리는 방법을 알아봅시다.

<br>

## 삼각함수 공식
<img src="https://user-images.githubusercontent.com/68521148/145054110-4aaf0d61-41d9-4711-ae24-b535efa27ebb.png" width="400" height="400"></img>

**@ = 각도, r = 반지름, a = 높이, b = 밑변**

```
Sin@: a / r => a(y좌표): Sin@ * r
Cos@: b / r => b(x좌표): Con@ * r
```

위 공식에서 Sin, Cos 와 a, b 위치를 바꾸어 x, y 좌표를 구한 후    
원은 360도. 원을 그리려면 0도와 360도 지점 좌표를 구해 Shape로 그려주면 되는데
세타(각도) 값을 각도법에서 호도법으로 변환해 넣어줘야 합니다.

**Math.PI = 3.14159265...** 

```
startRadian = 0도 * Math.PI / 180
endRadian = 360도 * Math.PI / 180
```

최종 C# 코드는

```C#
```








