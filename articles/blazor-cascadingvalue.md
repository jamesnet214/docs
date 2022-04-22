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

위의 코드에서 버튼을 클릭할 때마다 `currentCount`값이 1씩 증가하게 되며, 해당 값을 자식 컴포넌트에 넘겨주게 됩니다.

<br>

## Cascading Parameter

자식 컴포넌트에서 Cascading Value에 접근하기 위해서는 동일한 타입의 변수를 선언해주고 **`[CascadingParameter]`** 속성을 명시하면 됩니다.

#### `ChildCounter.razor`
```razor
<h4>Child Component Text - @ParentCount</h4>

@code {
    [CascadingParameter]
    protected int ParentCount { get; set; }
}
```

<img src="https://user-images.githubusercontent.com/74305823/164612965-c2bfb7cc-e54b-491b-83c5-ff5c7ebde270.gif"/>

<br>

## Multiple Cascading Parameters


<br>

## IsFixed Property

<br>

***

## References
- [Blazor cascading values and parameters](https://www.pragimtech.com/blog/blazor/blazor-cascading-values-parameters/)
- [ASP.NET Core Blazor cascading values and parameters](https://docs.microsoft.com/en-us/aspnet/core/blazor/components/cascading-values-and-parameters?view=aspnetcore-6.0)
