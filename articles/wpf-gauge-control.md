# WPF Gauge 컨트롤

<br>

## Chapter1 캔버스에 원 그리기

1. 유저컨트롤을 만들어 Canvas를 그려줍니다.

```C#
<Canvas x:Name="canvas" Width="150" Height="150"/>
```

2. Canvas 가운데 좌표값을 전역변수에 저장 해둡니다.

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
