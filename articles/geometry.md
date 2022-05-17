# Geometry

이 리포지토리는 Geometry 에 대하여 설명합니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br>

## Overview

Geometry가 WPF에 있어 시각적으로 차지하는 부분은 놀라울 정도로 방대합니다. 왜냐하면 우리가 실행한 WPF의 모든 시각적인 정보가 이것을 통해 표현되고 있기 때문인데요. 그런데 이렇게 깊은 부분까지 이해하고자 노력할 가치가 있을까요, 그렇다면 과연 이것을 제대로 이해하고 잘 활용한다면 WPF를 구사함에 있어 얼마나 도움이 될 수 있을까요? 

베일속에 가려져 있는 Geometry 클래스에 대해 자세하게 알아보는 시간을 준비했습니다.

## Geometry란 무엇인가?

WPF에서 Vector 기반의 그래픽을 그리기 위한 클래스입니다. 대표적으로 Path 객체를 통해 Geometry 타입의 Data 속성을 통해 아이콘 등의 그래픽을 표현할 수 있습니다.

<img width="376" alt="image" src="https://user-images.githubusercontent.com/52397976/168844624-6bdcd44e-f6de-43e3-8bba-252e299e8a4b.png">

그리고 Geometry와 비교 대상이 되는 **이미지**는 그림이 픽셀으로 표현되기 때문에 사이즈가 고정적인 반면, Geometry는 점과 선의 위치를 통해 표현되므로 크기에 구애받지 않고 반응형으로 깨지지 않고 표현할 수 있습니다.

> _Geometry 형식_ 
> `M17,8.5L12.25,12.32L17,16V8.5M4.7,18.4L2,16.7V7.7L5,6.7L9.3,10.03L18,2L22,4.5V20L17,22L9.34,14.66L4.7,18.4M5,14L6.86,12.28L5,10.5V14Z`

그렇기 때문에 Geometry는 사진 과 같은 Pixcel 기반의 표현에 적합하지 않습니다. 대신 `아이콘`이나 `선`, 특히 Material 풍의 디자인 요소를 표현하기에 아주 적합하며 다양한 해상도의 디스플레이가 제공되는 현 시점에서 가장 트랜디한 SVG Vector 기반의 표현을 Geometry를 통해 할 수 있는 것입니다.

| 축소 | 확대 |
|:----:|:----:|
| <img width="27" alt="image" src="https://user-images.githubusercontent.com/52397976/168847102-25af4d92-b7e4-4d57-9577-66bb2d93d422.png"> | <img width="181" alt="image" src="https://user-images.githubusercontent.com/52397976/168845107-3d837815-0bbd-411d-80a8-d2068daf2103.png"> | 


## Path 활용
Geometry는 자기 스스로 표현할 수가 없습니다. 그래서 Geometry를 사용할 수 있는 부모 객체가 필요한데 이게 바로 Path입니다. 우리가 흔히 알고 있는 SVG와같은 Vector 기반의 값을 사용할 있기 때문에 사용 빈도가 매우 높은 UI 객체중에 하나이기도 합니다.

#### 일반적인 사용 방법은 간단합니다.
```
<Path>
    <Path.Data>
        M17,8.5L12.25,12.32L17,16V8.5M4.7,18.4L2,16.7V7.7L5,6.7L9.3,10.03L18,2L22...
    </Path.Data>
</Path>
```
#### 또는
```
<Geometry x:Key="Icon1">M17,8.5L12.25,12.32L17,16V8.5M4.7,18.4L2,16.7V7.7L5,6.7L9.3,10.03L18,2L22...</Geometry>
...
<Path Data="{StaticResource Icon1}"/>
```
Path를 통해 Geometry를 사용하는 것은 이렇게나 간단합니다.

또 Geometry 사용이 가능한 객체는 Path 외에 몇 개가 더 있습니다.  
_`Path`를 포함해 Geometry 사용이 가능한 모든 객체들이 `Shape`으로부터 상속받고 있습니다._

- [x] **Path**
- [ ] Rectangle
- [ ] Ellipse
- [ ] Line
- [ ] Polyline
- [ ] Polygon

사실 Shape를 상속받는 클래스 중에서는 이미 사용해본 객체가 있을 것입니다. 사각형 Rectangle, 원 Ellipse 등 친숙한 도형들이 있는데 이것들도 사실 내부적으로 Geometry를 포함하고 있으며 그 형태가 Rectangle, Ellipse를 통해 정적으로 정해져있고 With, Height를 통해서만 사이즈를 변경할 수 있는 것입니다.

그래서 Path와 Shape를 더 깊이있게 알기 위해서는 Geometry의 세부 계층 구조를 들여다 봐야 합니다.
## Geometry 클래스 계층
Geometry 클래스는 총 7개의 파생된 Geometry를 가지고 있습니다. 
- LineGeometry
- RectangleGeometry
- EllipseGeometry
- GeometryGroup
- CombinedGeometry
- PathGeometry
- StreamGeometry

다음은 Geometry를 필두로 한 계층구조 모습입니다.
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
> ___Charles Petzold 中...___ 위의 클래스 계층도는 이번 장에서 다룰 순서대로 Geometry 파생 클래스들을 정렬해 보여준다. 이 클래스들은 WPF 그래픽이 순수 분석 기하학을 캡슐화하기 위해 기울인 노력을 가장 근접하게 설명해주는 결과물들이다. Geometry 객체는 점(points)과 길이(lengths)로 표현된다. Geometry 객체는 자신을 그리지 않는다. 원하는 브러시(Brush) 프로퍼티와 펜(pen) 프로퍼티로 Geometry 객체를 그리려면 별도의 클래스를(대부분의 경우 Path 클래스를) 사용해야 한다. 

Charles Petzold는 점(points)과 길이(lengths)를 통해 모든 그래픽 표현을 그릴 수 있도록 기하학을 캡슐화한 WPF 설계에 대해 위와 같이 묘사하고 있습니다. 그래서 보통 일반적으로는 Geometry를 사용하겠지만 파생된 7개의 다양한 하위 Geometry로 세분화되어 WPF를 표현하고 있다는 언급을 확인할 수 있습니다.

사실 Geometry를 상속받는 하위 객체들은 각각의 이름이 의미하는 것 처럼 사용하는 용도와 방식이 명확하게 정해져 있습니다. EllipseGeometry는 Ellipse와 같은 원을 표현하기 위해 특화된 Geometry이며, Rectangle은 사각형, Line은 선(Border 등에 사용되는데 이 얘기는 또 나중에...)을 그릴 때 쓰이고 있습니다.

그럼 이 중에서 가장 눈에 띄는 EllipseGeometry를 한번 살펴볼까요?

## EllipseGeometry
EllipseGeometry는 실제 Ellipse 객체 안에서 동작하고 있는 Geometry입니다.

그리고 실제 Ellipse 객체의 Geometry 관계를 살펴보면 이렇습니다.

```
Ellipse > EllipseGometry > Geometry
```

EllipseGeometry는 `Center`, `RadiusX`, `RadiusY` 3개의 프로퍼티 속성을 제공합니다. 이 객체에서 가장 중요한 **Center** 속성은 원의 가운데를 x축과 y축으로 결정하기 위한 Point Struct 타입입니다. 

| Center| RadiusX | RadiusY |
|:--:|:--:|:--:|
| Point { x: double, y: double } | double | double |
| 원의 가운데 지점 X, Y 좌표 | 센터를 기준으로 X축의 길이 | 센터를 기준으로 Y축의 길이 |
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

EllipseGeometry는 실제 점과 선의 값을 노출하지는 않지만 Center, RadiusY, RadiusX 값을 통해 내부적으로 Geometry를 그려 제공하게 됩니다.

![image](https://user-images.githubusercontent.com/52397976/162556691-6619dbef-025c-4c1a-83de-60a992c0eb38.png)

## RectangleGeometry
TBD...

## LineGeometry
TBD...

## StreamGeometry
TBD...





