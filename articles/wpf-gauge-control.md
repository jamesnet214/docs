# WPF Gauge 컨트롤

<br>

## Chapter1 캔버스에 원 그리기

1. 유저컨트롤을 만들어 Canvas를 그려줍니다.

```C#
<Canvas x:Name="canvas" Width="150" Height="150"/>
```

2. Canvas 가운데 좌표값(원의 반지름)을 전역변수에 저장 해둡니다.

```C#
public partial class NcoreDefaultGauge : UserControl
  {
      double cx;
      double cy;
      public NcoreDefaultGauge()
      {
          InitializeComponent();
          cx = canvas.Width / 2;
          cy = canvas.Height / 2;
      }
  }
```

3. 반지름, 시작각도(0) 끝각도(360) 값을 이용해 x1,y1 x2,y2 좌표를 얻습니다.

```C#
int start_anegle = 0, int end_angle = 360;

double startCos = (double)Math.Cos(start_angle * Math.PI / 180);
double startSin = (double)Math.Sin(start_angle * Math.PI / 180);

double endCos = (double)Math.Cos(end_angle * Math.PI / 180);
double endSin = (double)Math.Sin(end_angle * Math.PI / 180);

double xStart = cx + cx * startCos;
double yStart = cy + cy * startSin;

double xEnd = cx + cx * endCos;
double yEnd = cy + cy * endSin;
```

















