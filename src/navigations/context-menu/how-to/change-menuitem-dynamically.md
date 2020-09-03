---
title: "Change Menu Item Dynamically"
component: "Context Menu"
description: "This section helps to learn how to Change Menu Item Dynamically"
---

# Change Menu Item Dynamically

The items visible in the Context Menu can be changed dynamically based on the target. To achieve this behavior, initialize Context Menu with all items using [`Items`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Navigations.SfContextMenu-1.html#Syncfusion_Blazor_Navigations_SfContextMenu_1_Items) property and then you can Hide/Show items using [`HideItems`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Navigations.SfContextMenu-1.html#Syncfusion_Blazor_Navigations_SfContextMenu_1_HideItems_System_Collections_Generic_List_System_String__System_Boolean_)/[`ShowItems`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Navigations.SfContextMenu-1.html#Syncfusion_Blazor_Navigations_SfContextMenu_1_ShowItems_System_Collections_Generic_List_System_String__System_Boolean_) method in [`OnOpen`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Navigations.ContextMenuEvents-1.html#Syncfusion_Blazor_Navigations_ContextMenuEvents_1_OnOpen) event.

```csharp

@using Syncfusion.Blazor.Navigations

<div id="target">Right click/Touch hold to open the ContextMenu </div>
<SfContextMenu Target="#target" Items="MenuItems" @ref="ContextMenuObj">
    <ContextMenuEvents TValue="ContextMenuItem" OnOpen="Open"></ContextMenuEvents>
</SfContextMenu>

@code {
    SfContextMenu<ContextMenuItem> ContextMenuObj;
    public List<ContextMenuItem> MenuItems = new List<ContextMenuItem>
    {
        new ContextMenuItem{ Text = "Cut" },
        new ContextMenuItem{ Text = "Copy" },
        new ContextMenuItem{ Text = "Paste" },
        new ContextMenuItem{ Text = "Add" },
        new ContextMenuItem{ Text = "Edit" },
        new ContextMenuItem{ Text = "Delete" }
    };

    public List<string> HideItems = new List<string>() { "Cut", "Copy", "Paste"};

    public void Open(BeforeOpenCloseMenuEventArgs<ContextMenuItem> args)
    {
        this.ContextMenuObj.HideItems(this.HideItems);
    }
}

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

![Context Menu Sample](./../images/cm-dynamic.png)