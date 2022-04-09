# Geometry

Shape

- Rectangle
- Ellipse
- Line
- Polyline
- Polygon
- Path

Geometry 클래스 계층

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

> 위의 클래스 계층도는 이번 장에서 다룰 순서대로 Geometry 파생 클래스들을 정렬해 보여준다. 이 클래스들은 WPF 그래픽이 순수 분석 기하학을 캡슐화하기 위해 기울인 노력을 가장 근접하게 설명해주는 결과물들이다. Geometry 객체는 점(points)과 길이(lengths)로 표현된다. Geometry 객체는 자신을 그리지 않는다. 원하는 브러시(Brush) 프로퍼티와 펜(pen) 프로퍼티로 Geometry 객체를 그리려면 별도의 클래스를>(대부분의 경우 Path 클래스를) 사용해야 한다. _찰스페졸드의 WPF 에서..._
