# Material Design (3|U) components for Blazor
Since MudBlazor guys are not interested in moving to the latest material, I will port this thing to the Dynamic Color using [Bdziam.DynamicColor](https://github.com/pmikstacki/Bdziam.DynamicColor) 
I Previously worked on Bdziam.UI, which was started from scratch, but why bother? There are not so many differences. 

## Roadmap
- [ ] Rebuild Theming to adapt it to Material U Pallettes
- [ ] Rework some of the components (remove some old Material patterns/variants)
- [ ] Refactor Solution to stand on it's own (remove any references to MudBlazor since we're heading in completely different direction)
- [ ] Get rid of CSS StyleBuilder 
- [ ] Migrate from SCSS to incomponent styling
- [ ] Rework every component to match Material U Specification
- [ ] First *Stable* release

## But, Why? 
I like Material 3, It stands out from the crowd of mindless Themed Bootstrap / Tailwind drones that the landscape of web design has become. I want to bring this somehow exotic, somehow expressive design to blazor. 
I have some plans to create a fully featured product using this style, so you can be sure that I will work on this whenever I will find the time (I do a lot of sh$t lately, so be patient...)


## Diferrences from MudBlazor
I want to migrate to incomponent styling (of course using the (kinda like [](https://styled-components.com/) but for blazor - I know that solutions exist (Blazor Styled) but wait for it, and you'll be satisfied!)
Of course, whole Theming must be reworked. Some variants must be removed (like Normal TextField Variant or double iconed buttons) 

In the future I will be also trying to do the Material U Shapes (SkiaSharp so it will be performant) but thats far ahead of this time 





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
