---
layout: post
title: Change the text content & styles of Blazor ProgressButton | Syncfusion
description: Learn here all about changing the text content and styles of the Syncfusion Blazor ProgressButton component and more.
platform: Blazor
control: Progress Button
documentation: ug
---

# Change text content and styles of the Blazor ProgressButton Component

You can change the text content and styles of the Progress Button during progress state by changing the text content and the [CssClass](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.SplitButtons.SfProgressButton.html#Syncfusion_Blazor_SplitButtons_SfProgressButton_CssClass) property at the [OnBegin](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.SplitButtons.ProgressButtonEvents.html#Syncfusion_Blazor_SplitButtons_ProgressButtonEvents_OnBegin) and [OnEnd](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.SplitButtons.ProgressButtonEvents.html#Syncfusion_Blazor_SplitButtons_ProgressButtonEvents_OnEnd) events.

```cshtml

@using Syncfusion.Blazor.SplitButtons

<SfProgressButton Content="@Content" EnableProgress="true" CssClass="@CssClass" Duration="4000">
    <ProgressButtonEvents OnBegin="Begin" OnEnd="End"></ProgressButtonEvents>
</SfProgressButton>

@code {
    public string Content = "Upload";
    public string CssClass = "e-hide-spinner";
    public void Begin(Syncfusion.Blazor.SplitButtons.ProgressEventArgs args)
    {
        Content = "Uploading...";
        CssClass = "e-hide-spinner e-info";
    }
    public async Task End(Syncfusion.Blazor.SplitButtons.ProgressEventArgs args)
    {
        Content = "Success";
        CssClass = "e-hide-spinner e-success";
        await Task.Delay(1000);
        Content = "Upload";
        CssClass = "e-hide-spinner";
    }
}

```

Output be like

![Changing Text Content and Style of Blazor ProgressButton](./../images/blazor-progressbutton-change-text.png)