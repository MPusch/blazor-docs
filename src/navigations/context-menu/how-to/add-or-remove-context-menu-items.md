---
title: "Add or remove context menu items"
component: "Context Menu"
description: "This section helps to learn how to add or remove context menu items"
---

# Add or remove context menu items

Context Menu items can be added or removed using the [`InsertAfter`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Navigations.SfContextMenu-1.html#Syncfusion_Blazor_Navigations_SfContextMenu_1_InsertAfter_System_Collections_Generic_List__0__System_String_System_Boolean_), [`InsertBefore`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Navigations.SfContextMenu-1.html#Syncfusion_Blazor_Navigations_SfContextMenu_1_InsertBefore_System_Collections_Generic_List__0__System_String_System_Boolean_) and [`RemoveItems`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Navigations.SfContextMenu-1.html#Syncfusion_Blazor_Navigations_SfContextMenu_1_RemoveItems_System_Collections_Generic_List_System_String__System_Boolean_) methods.

In the following example, the **Display Settings** menu items are added before the **Personalize** item, the **Sort By** menu items are added after the **Refresh**, and the **Paste** item is removed from context menu.

```csharp

@using Syncfusion.Blazor.Navigations

<div id="target">Right click/Touch hold to open the ContextMenu </div>
<SfContextMenu Target="#target" Items="@MenuItems" @ref="ContextMenuObj">
    <ContextMenuEvents TValue="MenuItem" Created="create"></ContextMenuEvents>
</SfContextMenu>

@code {
    SfContextMenu<MenuItem> ContextMenuObj;
    public List<MenuItem> MenuItems = new List<MenuItem>
    {
        new MenuItem{ Text="View", Items= new List<MenuItem>{
        new MenuItem { Text="Large Icons"},
        new MenuItem { Text="Medium Icons"},
        new MenuItem { Text="Small Icons"} } },
        new MenuItem{ Text="Refresh" },
        new MenuItem{ Text="Paste" },
        new MenuItem{ Separator=true },
        new MenuItem{ Text="New" },
        new MenuItem{ Separator=true},
        new MenuItem{ Text="Personalize"}
    };
    public List<string> RemoveItem = new List<string>() { "Paste" };
    public List<MenuItem> InsertAfterItem = new List<MenuItem>
    {
        new MenuItem{Text = "Sort By"}
    };
    public List<MenuItem> InsertBeforeItem = new List<MenuItem>
    {
        new MenuItem{Text = "Display Settings"}
    };
    private void create(object obj)
    {
        ContextMenuObj.InsertAfter(this.InsertAfterItem, "Refresh");
        ContextMenuObj.InsertBefore(this.InsertBeforeItem, "Personalize");
        ContextMenuObj.RemoveItems(this.RemoveItem);
    }
};

<style>
#target {
    border: 1px dashed;
    height: 150px;
    padding: 10px;
    position: relative;
    text-align: justify;
    color: gray;
    user-select: none;
}
</style>

```

Output be like

![Context Menu Sample](./../images/cm-add.png)