---
title: "Group popup items with ListView component"
component: "Dropdown Menu"
description: " This section explains how to group popup items using list view component in Blazor."
---

# Group popup items with ListView component

Header in popup items is possible in Dropdown Menu by templating entire popup with ListView. Create ListView with [`ID`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Lists.SfListView-1.html#Syncfusion_Blazor_Lists_SfListView_1_ID) listview and provide it as a [`Target`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.SplitButtons.SfSplitButton.html) for Dropdown Menu.

In the following example, ListView element is given as `Target` to Dropdown Menu and header can be achieved
by [`GroupBy`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Lists.FieldSettingsModel.html#Syncfusion_Blazor_Lists_FieldSettingsModel_GroupBy) property.

```csharp

@using Syncfusion.Blazor.SplitButtons
@using Syncfusion.Blazor.Lists

<SfDropDownButton Target="#listview" CssClass="e-caret-hide" IconCss="e-icons e-down"></SfDropDownButton>
<SfListView ID="listview" DataSource="@Data" ShowCheckBox="true">
    <ListViewFieldSettings Text="Text" GroupBy="Category"></ListViewFieldSettings>
</SfListView>

@code {
    public List<ListData> Data = new List<ListData>{
        new ListData{ Class = "data", Text = "Print", Id = "data1", Category = "Customize Quick Access Toolbar" },
        new ListData{ Class = "data", Text = "Save As", Id = "data2", Category = "Customize Quick Access Toolbar" },
        new ListData{ Class = "data", Text = "Update Folder", Id = "data3", Category = "Customize Quick Access Toolbar"},
        new ListData{ Class = "data", Text = "Reply", Id = "data4", Category = "Customize Quick Access Toolbar" }
};

    public class ListData
    {
        public string Text { get; set; }
        public string Id { get; set; }
        public string Class { get; set; }
        public string Category { get; set; }
    }
}

<style>
    .e-down::before {
    content: '\e744';
}
</style>

```

Output be like

![Button Sample](./../images/ddb-listview.png)