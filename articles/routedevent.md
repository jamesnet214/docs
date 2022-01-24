## RoutedEvent

이 리포지토리는 RoutedEvent에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/docs/stargazers"><img src="https://img.shields.io/github/stars/devncore/docs" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/docs" alt="License"> | <a href="https://github.com/devncore/docs/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/docs" alt="Commits-per-month"></a> |

<br />

### RoutedEvent 란?
RoutedEvent를 통해 Control에 대한 이벤트를 처리를 할 때 이벤트를 발생시킨 개체와 관계된 상위 요소를 호출할 수 있는 이벤트 형식입니다. 
이벤트를 발생시킨 개체부터 루트에 도달 할 때까지 상위 요소로 가는경로를 버블링(Bubbling) 이라하며 터널링(Tunneling)이라고 합니다.
이벤트 라우팅은 어떤 이벤트가 컨트롤의 하위 또는 상위로 전달되는 것 을 이야기하며 WPF에서 광범위하게 이용되는 방법입니다.

<br />

### RoutedEvent 처리순서도

| 이벤트 처리순서도|
|:-:|
| ![image](https://user-images.githubusercontent.com/76234292/150774551-45e7b3ca-1677-41b8-9f33-f90616587e3c.png) |

<br />

### Event 종류
- Directed Event
- Bubbling Event
- Tunnel Event

<br />

#### Directed
Object가 Event를 발생 시키고 직접 처리하는 방식 입니다.
소스 요소 자체만 응답으로 처리기 호출이 가능합니다.

<br />

#### Bubbling
일반적인 이름을 가지는 이벤트는 버블링 이벤트로 동작한다.
이벤트 발생시 하위 요소부터 이벤트가 발생합니다.

<br />

#### Tunnel
이벤트 앞에 Preview 를 붙인 이벤트는 터널링 이벤트로 동작한다.
이벤트 발생시 상위에 요소부터 이벤트가 발생합니다.
주로 사용되는 이벤트로는 PreviewMouseDown, PreviewDragDown 등이 있으며 Preview 가 쓰여지는 것들을 Tunneling 이벤트라고 이해하면 됩니다.

<br />
