# Inline Rendering

By default, the ColorPicker will be rendered using SplitButton and open the pop-up to access the ColorPicker. To render the ColorPicker container alone and to access it directly, render it as inline. It can be achieved by setting the [`Inline`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Inputs.SfColorPicker.html#Syncfusion_Blazor_Inputs_SfColorPicker_Inline) property to `true`.

The following sample shows the inline type rendering of ColorPicker.

```csharp
@using Syncfusion.Blazor.Inputs

<h4>Choose a color</h4>
<SfColorPicker Value="035a" Inline="true" ShowButtons="false"></SfColorPicker>
```

Output be like
![color-picker](./images/inline-rendering.png)

>> The `ShowButtons` property is disabled in this sample because the control buttons are not needed for inline type. To know about the control buttons functionality, refer to the [`ShowButtons`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Inputs.SfColorPicker.html#Syncfusion_Blazor_Inputs_SfColorPicker_ShowButtons).
