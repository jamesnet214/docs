## WPF Gauge Control

이 리포지토리는 WPF Gauge Control에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

1. UserControl 안에 Canvas를 그립니다.

```C#
<Canvas x:Name="canvas" Width="150" Height="150"/>
```

<br />

2. Canvas 정중앙의 좌표값(원의 반지름)을 전역변수에 저장합니다.

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

<br />

3. 반지름, 시작각도(0), 끝각도(360) 값을 이용해 원의 시작점좌표와 끝점좌표를 구한 후 DrawInfo 클래스에 저장합니다.

<br />

4. 앞서 만든 DrawInfo 데이터를 이용하여 DrawShape 클래스 내에서 Geometry를 그려 준 후 Canvas의 Children에 추가합니다.

<br />

### 전체 소스 및 결과물

> **MainWindow.xaml**

```xaml
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
```

<br />

> **NcoreDefaultGauge.xaml**

```xaml
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

<br />

> **NcoreDefaultGauge.xaml.cs**

```csharp
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

<br />

> **DrawInfo.cs**

```csharp
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

<br />

> **DrawShape.cs**  

TBD...

![image](https://user-images.githubusercontent.com/68521148/144867890-8ac87c23-662c-4a29-ad32-d70ff3d48fae.png)
