# MudBlazor
> MudBlazor는 Blazor를 위한 Material Design 컴포넌트 프레임워크입니다.

👉 **[MudBlazor GitHub](https://github.com/MudBlazor/MudBlazor)**

<br/>

## Getting Started

#### 1. 패키지 설치
Nuget Package Manager에서 `MudBlazor` 패키지를 찾아 설치하거나, 아래 명령을 입력해 설치합니다.
```
dotnet add package MudBlazor
```

#### 2. Imports 추가
**`_Imports.razor`** 파일 안에 MudBlazor를 추가합니다.
```cshtml
@using MudBlazor
```

#### 3. Style 추가
**`index.html`** 혹은 **`_Layout.cshtml`** / **`_Host.cshtml`** 파일 내 HTML head 부분에 아래 내용을 추가합니다.
```html
<link href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap" rel="stylesheet" />
<link href="_content/MudBlazor/MudBlazor.min.css" rel="stylesheet" />
```

예시: **`_Layout.cshtml`**
```html
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>@ViewData["Title"] - RazorApp</title>
    <link rel="stylesheet" href="~/lib/bootstrap/dist/css/bootstrap.min.css" />
    <link rel="stylesheet" href="~/css/site.css" asp-append-version="true" />
    <link rel="stylesheet" href="~/RazorApp.styles.css" asp-append-version="true" />
    <link href="~/css/style.css" rel="stylesheet" asp-append-version="true" />
    
    @*MudBlazor Style Reference*@
    <link href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap" rel="stylesheet" />
    <link href="_content/MudBlazor/MudBlazor.min.css" rel="stylesheet" />
</head>
```

#### 4. script 추가
앞서 Style을 추가한 파일과 동일한 파일에 MudBlazo js file을 추가합니다. Blazor의 기본 스크립트의 위치와 동일해야 합니다.
```html
<script src="_content/MudBlazor/MudBlazor.min.js"></script>
```

예시: **`_Layout.cshtml`**
```html
<body>
    ...
    <script src="_framework/blazor.server.js"></script>
    @*MudBlazor Script Reference*@
    <script src="/_content/MudBlazor/MudBlazor.min.js"></script>
</head> 
```

#### 5. 서비스 등록
**`Program.cs`** 파일에 아래 내용을 추가합니다. _(.NET 6 기준)_
```csharp
using MudBlazor.Services;

builder.Services.AddMudServices();
```

#### 6. 컴포넌트 추가
**`MainLayout.razor`** 파일 안에 아래 컴포넌트들을 추가합니다. `ThemeProvider`는 MudBlazor 사용을 위해 필수로 있어야 하지만, 나머지는 선택적으로 사용할 수 있습니다.
```razor
<MudThemeProvider/>
<MudDialogProvider/>
<MudSnackbarProvider/>
```
