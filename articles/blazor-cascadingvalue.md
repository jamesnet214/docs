# Blazor Cascading Value

## Contents
- [개요](#개요)
- [Cascading Value Component](#cascading-value-component)
- [Cascading Parameter](#cascading-parameter)
- [Multiple Cascading Parameters](#multiple-cascading-parameters)
- [IsFixed Property](#isfixed-property)

<br>

## 개요
Blazor App은 컴포넌트의 집합입니다. 개별 컴포넌트를 만들고 그것들을 함께 배치하여 Blazor App을 만들 수 있습니다. 
'A' 컴포넌트는 'B' 컴포넌트 안에서 사용될 수 있고, 'B' 컴포넌트는 또 다른 컴포넌트 안에서 사용될 수 있습니다.

이처럼 여러 컴포넌트들이 계층구조를 가지고 있을 때, 컴포넌트 파라미터를 이용하여 부모 컴포넌트에서 자식 컴포넌트로 데이터를 넘겨줘야 할 경우가 있습니다.
이때 사용할 수 있는 것이 **Cascading Value**와 **Cascading Parameter**입니다.

<br>

## Cascading Value Component
Blazor는 **`CascadingValue`** 라는 내장 컴포넌트를 가지고 있습니다. 이 컴포넌트를 이용해 자식 컴포넌트에 데이터를 넘겨줄 수 있습니다.

![image](https://user-images.githubusercontent.com/74305823/164609018-1ab8e2d8-a6a9-498d-bc97-5fb8168f45d5.png)

아래의 코드에서 버튼을 클릭할 때마다 `currentCount`값이 1씩 증가하게 되며, 해당 값을 자식 컴포넌트에 넘겨주게 됩니다.
```razor
@page "/counter"

<h1>Counter</h1>

<p>
    <button class="btn btn-primary" @onclick="IncrementCount">Click</button>
</p>

<CascadingValue Value="@currentCount">
    <ChildCounter></ChildCounter>
</CascadingValue>

@code {
    private int currentCount { get; set; } = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}
```

<br>

## Cascading Parameter

자식 컴포넌트에서 Cascading Value에 접근하기 위해서는 동일한 타입의 변수를 선언해주고 **`[CascadingParameter]`** 속성을 명시하면 됩니다.

#### `ChildCounter.razor`
```razor
<h4>Child Component Text - @ParentCount</h4>

@code {
    [CascadingParameter]
    public int ParentCount { get; set; }
}
```

<img src="https://user-images.githubusercontent.com/74305823/164612965-c2bfb7cc-e54b-491b-83c5-ff5c7ebde270.gif"/>

<br>

## Multiple Cascading Parameters

- #### Cascading Value들의 Type이 다를 경우

아래의 코드에서 Cascading Value는 `int` 타입의 **`currentCount`** 와 `string` 타입의 **`style`** 입니다.
```razor
@page "/counter"

<h1>Counter</h1>

<p>
    <button class="btn btn-primary" @onclick="IncrementCount">Click</button>
</p>

<CascadingValue Value="@style">
    <CascadingValue Value="@currentCount">
        <ChildCounter></ChildCounter>
    </CascadingValue>
</CascadingValue>

@code {
    private int currentCount { get; set; } = 0;
    private string style { get; set; } = "color:red";

    private void IncrementCount()
    {
        currentCount++;
    }
}
```

#### `ChildCounter.razor`

부모 컴포넌트로부터 전달받은 두 개의 Value 타입이 다르므로, 자식 컴포넌트에서는 각 변수를 선언해주고 `[CascadingParameter]` 속성을 명시해주면 
동일한 타입의 변수값을 받을 수 있습니다.

```razor
<h4 style="@ElementStyle">Child Component Text - @ParentCount</h4>

@code {
    [CascadingParameter]
    public int ParentCount { get; set; }
    
    [CascadingParameter]
    public string ElementStyle { get; set; }
}
```

<img src="https://user-images.githubusercontent.com/74305823/164618477-1a645e87-058e-4a6d-8226-6e7ead312982.png" width="600"/>

<br>

- #### Cascading Value들의 Type이 같을 경우

아래의 코드에서 Cascading Value는 **`style`** 과 **`borderStyle`** 이며, 둘 다 `string` 타입입니다.
```razor
<CascadingValue Value="@style">
    <CascadingValue Value="@borderStyle">
        <ChildCounter></ChildCounter>
    </CascadingValue>
</CascadingValue>

@code {
    private string style { get; set; } = "color:red";
    private string borderStyle { get; set; } = "border:1px solid red";
}
```

#### `ChildCounter.razor`

자식 컴포넌트에서는 **`ElementStyle`** 이라는 변수를 선언하여 부모 컴포넌트로부터 Value값을 가져올 것입니다.
```razor
<h4 style="@ElementStyle">Child Component Text</h4>

@code {
    [CascadingParameter]
    public string ElementStyle { get; set; }
}
```

<img src="https://user-images.githubusercontent.com/74305823/164620080-02942d5f-7064-4719-b2b9-072818d816cb.png" width="600"/>

실행 결과, **`ElementStyle`** 변수는 부모의 **`borderStyle`** 값을 받았습니다. 이는 동일한 변수 타입의 Cascading Value가 있을 때, 
자식 컴포넌트와 더 가깝게 위치한 Value값이 우위를 차지하기 때문입니다.

<br>

#### `ChildCounter.razor`

자식 컴포넌트에 **`BorderStyle`** 이라는 CascadingParameter를 하나 더 생성해보겠습니다.

```razor
<h4 style="@ElementStyle; @BorderStyle">Child Component Text</h4>

@code {
    [CascadingParameter]
    public string ElementStyle { get; set; }
    
    [CascadingParameter]
    public string BorderStyle { get; set; }
}
```
![image](https://user-images.githubusercontent.com/74305823/164623878-924373a7-6944-4159-8e80-8dffc93c27eb.png)

실행 결과, **`ElementStyle`** 과 **`BorderStyle`** 둘 다 부모의 **`borderStyle`** 값을 받은 것을 확인할 수 있습니다. 
앞서 보았던 결과와 마찬가지로 부모 컴포넌트의 **`borderStyle`** 값이 자식 컴포넌트와 더 가깝게 위치하여 우위를 차지했기 때문입니다.

<br>

#### 🤔 _그렇다면 각각 다른 Value값을 받으려면 어떻게 해야 할까요?_

이때는 아래 코드와 같이 CascadingValue 컴포넌트의 `Name` 속성으로 접근할 수 있습니다.
```razor
<CascadingValue Value="@style" Name="ColorStyle">
    <CascadingValue Value="@borderStyle" Name="BorderStyle">
        <ChildCounter></ChildCounter>
    </CascadingValue>
</CascadingValue>

@code {
    private string style { get; set; } = "color:red";
    private string borderStyle { get; set; } = "border:1px solid red";
}
```

#### `ChildCounter.razor`

부모 컴포넌트에서 선언한 CascadingValue컴포넌트의 `Name`값을 CascadingParameter에 명시하여, 각각 어떤 속성값을 전달받을 것인지 결정할 수 있습니다.

```razor
<h4 style="@ElementStyle; @BorderStyle">Child Component Text</h4>

@code {
    [CascadingParameter (Name = "ColorStyle")]
    public string ElementStyle { get; set; }

    [CascadingParameter (Name = "BorderStyle")]
    public string BorderStyle { get; set; }
}
```

<img src="https://user-images.githubusercontent.com/74305823/164625885-8b90b1cc-2a63-4143-bdd3-ee1e08a553c0.png" width="750"/>

실행 결과, 부모 컴포넌트의 `style`과 `borderStyle`이 각각 적용된 것을 확인할 수 있습니다.

<br>

## IsFixed Property

<br>

***

## References
- [Blazor cascading values and parameters](https://www.pragimtech.com/blog/blazor/blazor-cascading-values-parameters/)
- [ASP.NET Core Blazor cascading values and parameters](https://docs.microsoft.com/en-us/aspnet/core/blazor/components/cascading-values-and-parameters?view=aspnetcore-6.0)
