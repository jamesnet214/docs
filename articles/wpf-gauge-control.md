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
   
### 전체 소스 및 결과물

- MainWindow.xaml

```C#
<Window x:Class="WpfGaugeExam.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfGaugeExam"
        xmlns:ctrls="clr-namespace:WpfGaugeExam.Controls"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <Grid>
        <ctrls:NcoreDefaultGauge/>
    </Grid>
</Window>

- NcoreDefaultGauge.xaml

```C#
<UserControl x:Class="WpfGaugeExam.Controls.NcoreDefaultGauge"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
             xmlns:local="clr-namespace:WpfGaugeExam.Controls"
             mc:Ignorable="d" 
             d:DesignHeight="450" d:DesignWidth="800">
    <Grid>
        <Canvas x:Name="canvas" Width="150" Height="150"/>
    </Grid>
</UserControl>
```

- NcoreDefaultGauge.xaml.cs

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
using WpfGaugeExam.Models;
using WpfGaugeExam.DrawHelper;

namespace WpfGaugeExam.Controls
{
    /// <summary>
    /// NcoreDefaultGauge.xaml에 대한 상호 작용 논리
    /// </summary>
    public partial class NcoreDefaultGauge : UserControl
    {
        double cx;
        double cy;
        public NcoreDefaultGauge()
        {
            InitializeComponent();
            cx = canvas.Width / 2;
            cy = canvas.Height / 2;

            double start_angle = 0, end_angle = 359.99999;
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
            shape.Fill = Brushes.Pink;
            canvas.Children.Add(shape);
        }
    }
}
```

- DrawInfo.cs

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace WpfGaugeExam.Models
{
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
}
```

- DrawShape.cs

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
using WpfGaugeExam.Models;
using WpfGaugeExam.DrawHelper;

namespace WpfGaugeExam.Controls
{
    /// <summary>
    /// NcoreDefaultGauge.xaml에 대한 상호 작용 논리
    /// </summary>
    public partial class NcoreDefaultGauge : UserControl
    {
        double cx;
        double cy;
        public NcoreDefaultGauge()
        {
            InitializeComponent();
            cx = canvas.Width / 2;
            cy = canvas.Height / 2;

            double start_angle = 0, end_angle = 359.99999;
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
            shape.Fill = Brushes.Pink;
            canvas.Children.Add(shape);
        }
    }
}
```
![image](https://user-images.githubusercontent.com/68521148/144867890-8ac87c23-662c-4a29-ad32-d70ff3d48fae.png)

















