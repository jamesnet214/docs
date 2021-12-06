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

3. 반지름, 시작각도(0) 끝각도(360) 값을 이용해 x1,y1 x2,y2 좌표를 얻어 DrawInfo 클래스를 만든 후    
   정보들 담아주고 Shape를 상속받은 DrawShape클래스를 만든후 DrawShape클래스 내에서 DrawInfo 데이터를 가지고    
   원 Geometry를 그려 준 후 Canvas의 Children에 넣어줍니다.
```C#
public class DrawInfo
{      
    public double XStart { get; set; }
    public double YStart { get; set; }
    public double XEnd { get; set; }
    public double YEnd { get; set; }
    public double ArcR { get; set; }
    public double StartAngle { get; set; }
    public double EndAngle { get; set; }

}
```

```C#
int start_angle = 0, end_angle = 360;
DrawInfo drawInfo = new DrawInfo();

double startCos = (double)Math.Cos(start_angle * Math.PI / 180);
double startSin = (double)Math.Sin(start_angle * Math.PI / 180);

double endCos = (double)Math.Cos(end_angle * Math.PI / 180);
double endSin = (double)Math.Sin(end_angle * Math.PI / 180);

drawInfo.XStart = cx + cx * startCos;
drawInfo.YStart = cy + cy * startSin;

drawInfo.XEnd = cx + cx * endCos;
drawInfo.YEnd = cy + cy * endSin;

drawInfo.ArcR = cx;
drawInfo.StartAngle = start_angle;
drawInfo.EndAngle = end_angle;

DrawShape shape = new DrawShape(drawInfo);
canvas.Children.Add(shape);
```

```C#
public class DrawShape : Shape
{

    DrawInfo _DrawInfo = new DrawInfo();
    protected override Geometry DefiningGeometry { get { return GetGeometry(); } }

    public DrawShape(DrawInfo _drawInfo)
    {
        _DrawInfo = _drawInfo;
    }

    private Geometry GetGeometry()
    {
        StreamGeometry geom = new StreamGeometry();
        using (StreamGeometryContext ctx = geom.Open())
        {
            ctx.BeginFigure(
                new Point(_DrawInfo.XStart,
                          _DrawInfo.YStart),
                true,   // Filled
                false);  // Closed
            ctx.ArcTo(
                new Point(_DrawInfo.XEnd,
                          _DrawInfo.YEnd),
                new Size(_DrawInfo.ArcR, _DrawInfo.ArcR),
                0.0,     // rotationAngle
                _DrawInfo.EndAngle - _DrawInfo.StartAngle > 180,   //그려지는 각도가 180도 넘는지 체크
                SweepDirection.Clockwise, //시계방향으로 그림
                true,    // isStroked
                false);
        }

        return geom;
    }
}
```

















