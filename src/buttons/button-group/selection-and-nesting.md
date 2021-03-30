# Selection and Nesting

## Single selection

ButtonGroup supports single selection type in which only one button can be selected.

The following example illustrates the single selection behavior in ButtonGroup.

```csharp

@using Syncfusion.Blazor.SplitButtons

<SfButtonGroup Mode="SelectionMode.Single">
    <ButtonGroupButton>Left</ButtonGroupButton>
    <ButtonGroupButton @bind-Selected="@centerSelected">Center</ButtonGroupButton>
    <ButtonGroupButton>Right</ButtonGroupButton>
</SfButtonGroup>

@code {
    private bool centerSelected = true;
}

```

Output be like

![ButtonGroup Sample](./images/single.png)

## Multiple selection

ButtonGroup supports multiple selection type in which multiple button can be selected.

The following example illustrates the multiple selection behavior in ButtonGroup.

```csharp
@using Syncfusion.Blazor.SplitButtons

<SfButtonGroup Mode="SelectionMode.Multiple">
    <ButtonGroupButton @bind-Selected="@boldSelected" IconCss="bg-icons e-btngrp-bold">Bold</ButtonGroupButton>
    <ButtonGroupButton @bind-Selected="@italicSelected" IconCss="bg-icons e-btngrp-italic e-icon-left">Italic</ButtonGroupButton>
    <ButtonGroupButton IconCss="bg-icons e-btngrp-underline e-icon-left">Underline</ButtonGroupButton>
</SfButtonGroup>

@code {
    private bool boldSelected = true;
    private bool italicSelected = true;
}

```

Output be like

![ButtonGroup Sample](./images/multiple.png)

## Nesting

Nesting with other components can be possible in ButtonGroup. The following components can be nested in ButtonGroup.
* DropDownButton
* SplitButton

### DropDownButton

In the following example, the DropDownButton component can be added in ButtonGroup tag.

```csharp
@using Syncfusion.Blazor.SplitButtons

  <SfButtonGroup>
    <ButtonGroupButton CssClass="e-btn e-success">View</ButtonGroupButton>
    <ButtonGroupButton CssClass="e-btn e-success">Edit</ButtonGroupButton>
        <SfDropDownButton Content="Profile">
            <DropDownMenuItems>
                <DropDownMenuItem Text="Dashboard"></DropDownMenuItem>
                <DropDownMenuItem Text="Notifications"></DropDownMenuItem>
                <DropDownMenuItem Text="User Settings"></DropDownMenuItem>
                <DropDownMenuItem Text="Log Out"></DropDownMenuItem>
            </DropDownMenuItems>
        </SfDropDownButton>
</SfButtonGroup>

```

Output be like

![ButtonGroup Sample](./images/dropdown.png)

### SplitButton

In the following example, SplitButton component can be added in ButtonGroup tag.

```csharp
@using Syncfusion.Blazor.SplitButtons

  <SfButtonGroup>
    <ButtonGroupButton CssClass="e-btn e-success">View</ButtonGroupButton>
    <ButtonGroupButton CssClass="e-btn e-success">Edit</ButtonGroupButton>
        <SfSplitButton Content="Paste">
            <DropDownMenuItems>
                <DropDownMenuItem Text="Paste"></DropDownMenuItem>
                <DropDownMenuItem Text="Paste Special"></DropDownMenuItem>
                <DropDownMenuItem Text="Paste as Formula"></DropDownMenuItem>
                <DropDownMenuItem Text="Paste as Hyperlink"></DropDownMenuItem>
            </DropDownMenuItems>
        </SfSplitButton>
</SfButtonGroup>
```

Output be like

![ButtonGroup Sample](./images/splitbutton.png)