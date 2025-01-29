# Material Design (3|U) components for Blazor
Since MudBlazor guys are not interested in moving to the latest material, I will port this thing to the Dynamic Color using Bdziam.DynamicColor. 

### Quick Installation Guide
Install Package
```
dotnet add package Bdziam.MudBlazor
```
Add the following to `_Imports.razor`
```razor
@using MudBlazor
```
Add the following to the `MainLayout.razor` or `App.razor`
```razor
<MudThemeProvider/>
<MudPopoverProvider/>
<MudDialogProvider/>
<MudSnackbarProvider/>
```
Add the following to your HTML `head` section, it's either `index.html` or `_Layout.cshtml`/`_Host.cshtml`/`App.razor` depending on whether you're running WebAssembly or Server
```razor
<link href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap" rel="stylesheet" />
<link href="_content/MudBlazor/MudBlazor.min.css" rel="stylesheet" />
```
Next, add the following to the default Blazor script at the end of the `body`
```razor
<script src="_content/MudBlazor/MudBlazor.min.js"></script>
```

Add the following to the relevant sections of `Program.cs`
```c#
using MudBlazor.Services;
```
```c#
builder.Services.AddMudServices();
```

### Usage
```razor
<MudText Typo="Typo.h6">
    MudBlazor is @Text
</MudText>

<MudButton Variant="Variant.Filled" 
           Color="Color.Primary" 
           OnClick="ButtonOnClick">
    @ButtonText
</MudButton>

@code {
    string Text { get; set; } = "????";
    string ButtonText { get; set; } = "Click Me";
    int ClickCount { get; set; }

    void ButtonOnClick()
    {
        ClickCount += 1;
        Text = $"Awesome x {ClickCount}";
        ButtonText = "Click Me Again";
    }
}
```
