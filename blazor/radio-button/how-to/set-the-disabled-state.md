---
layout: post
title: Set the disabled state in Blazor RadioButton Component | Syncfusion
description: Checkout and learn here all about Set the disabled state in Syncfusion Blazor RadioButton component and more.
platform: Blazor
control: Radio Button
documentation: ug
---

# Set the disabled state in Blazor RadioButton Component

Radio Button component can be enabled/disabled by giving [Disabled](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Buttons.SfRadioButton-1.html) property. To disable Radio Button component, the `Disabled` property can be set as `true`.

```cshtml
@using Syncfusion.Blazor.Buttons

<SfRadioButton Label="Option 1" Name="default" Value="Checked" @bind-Checked="stringChecked"></SfRadioButton><br />
<SfRadioButton Label="Option 2" Name="default" Value="Disable" @bind-Checked="stringChecked" Disabled="true"></SfRadioButton><br />
<SfRadioButton Label="Option 3" Name="default" Value="None" @bind-Checked="stringChecked"></SfRadioButton>

@code {
    private string stringChecked = "Checked";
}

```

Output be like

![Blazor RadioButton in Disable State](./../images/blazor-radiobutton-disable-state.png)