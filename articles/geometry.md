# Overview

WPF에서 Geometry가 시각적으로 차지하는 역할은 상상 그 이상일 것입니다.  

그 이유는 우리가 실행한 WPF 앱의 거의 모든 시각적인 정보를 바로 이 **Geometry**가 그렸다고 해도 과장이 아니기 때문이죠. 그렇다면 이 클래스를 제대로 이해하고 잘 활용할 수만 있다면 무슨 일을 할 수 있을까요? 

단조로운 표현에서 벗어날 수 있습니다.

그럼 우리가 잘 몰랐던 Geometry 클래스에 대해 자세하게 알아보는 시간을 가져보겠습니다.

## Geometry란 무엇인가요?

WPF에서 Vector 기반의 그래픽을 그리기 위한 클래스입니다.  

좀 더 대단하게 표현하고 싶지만 달리 설명하기가 어렵군요. Geometry는 WPF에서 시각적인 나타냄을 하기 위한 가장 기본 단위의 표현이라고 생각하면 됩니다. 왜 그런지에 대해서는 좀 더 이야기 해나가 봅시다. 


## Shape를 상속받는 클래스
Shape를 상속받으면서 동시에 Geometry를 표현할 수 있는 클래스입니다.

```
- Rectangle
- Ellipse
- Line
- Polyline
- Polygon
- Path
```

## Geometry 클래스 계층
Geometry 클래스는 총 7개의 파생된 Geometry를 가지고 있습니다. 
> LineGeometry, RectangleGeometry, CombinedGeometry, PathGeometry, StreamGeometry

```
- Object
  - DispatcherObject (abstract)
    - DependencyObject
      - Freezable (abstract)
        - Animatable
          - Geometry
            - LineGeometry
            - RectangleGeometry
            - EllipseGeometry
            - GeometryGroup
            - CombinedGeometry
            - PathGeometry
            - StreamGeometry
```

> 위의 클래스 계층도는 이번 장에서 다룰 순서대로 Geometry 파생 클래스들을 정렬해 보여준다. 이 클래스들은 WPF 그래픽이 순수 분석 기하학을 캡슐화하기 위해 기울인 노력을 가장 근접하게 설명해주는 결과물들이다. Geometry 객체는 점(points)과 길이(lengths)로 표현된다. Geometry 객체는 자신을 그리지 않는다. 원하는 브러시(Brush) 프로퍼티와 펜(pen) 프로퍼티로 Geometry 객체를 그리려면 별도의 클래스를(대부분의 경우 Path 클래스를) 사용해야 한다. 

___Charles Petzold 中...___

윈버지 **Charles Petzold**는 점(points)과 길이(lengths)를 통해 모든 그래픽 표현을 그릴 수 있도록 기하학을 캡슐화한 WPF 설계를 언급하고 있습니다.


## EllipseGeometry
EllipseGeometry는 `Center`, `RadiusX`, `RadiusY` 3개의 프로퍼티 속성을 제공합니다. 이 객체에서 가장 중요한 **Center** 속성은 원의 가운데를 x축과 y축으로 결정하기 위한 Point Struct 타입입니다. 

| Center| RadiusX | RadiusY |
|:--:|:--:|:--:|
| Point { x: double, y: double } | double | double |
| 원의 가운데 지점을 x, y 좌표 형태로 나타냅니다. | | |
| Center="50, 50" | RadiusX="48" | RadiusY="48" |

```xaml
<Window x:Class="EllipseGeometryTest.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:EllipseGeometryTest"
        mc:Ignorable="d"
        Title="MainWindow" SizeToContent="WidthAndHeight">
    <Viewbox Margin="10">
        <Path StrokeThickness="4" 
              Stroke="#222222" 
              Width="100" 
              Height="100" 
              Fill="#353535">
            <Path.Data>
                <EllipseGeometry Center="50, 50" RadiusX="48" RadiusY="48"/>
            </Path.Data>
        </Path> 
    </Viewbox>
</Window>
```

![image](https://user-images.githubusercontent.com/52397976/162556691-6619dbef-025c-4c1a-83de-60a992c0eb38.png)

