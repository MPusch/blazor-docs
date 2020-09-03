---
title: "Data Binding"
component: "Contex tMenu"
description: "This section helps to learn how to bind data"
---

# Data Binding

To bind local data source to the Context Menu, menu items are populated from data source and mapped to [`Items`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Navigations.SfContextMenu-1.html#Syncfusion_Blazor_Navigations_SfContextMenu_1_Items) property. In the following example, data given in `CustomItems.cs` file is mapped to `Items` property.

```csharp

@using Syncfusion.Blazor.Navigations

<div id="target">Right click/Touch hold to open the ContextMenu </div>
<SfContextMenu Target="#target" Items="@CustomItems.GetItems()"></SfContextMenu>

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

`CustomItems.cs`

```csharp

using System.Collections.Generic;
public class CustomItems
    {
        public CustomItems()
        {

        }

        public CustomItems(string Text, string Id)
        {
            this.Text = Text;
            this.Id = Id;
        }

        public string Text { get; set; }
        public string Id { get; set; }
        public static List<CustomItems> GetItems()
        {
            List<CustomItems> Items = new List<CustomItems>();
            Items.Add(new CustomItems { Text = "Cut", Id = "1" });
            Items.Add(new CustomItems { Text = "Copy", Id = "2" });
            Items.Add(new CustomItems { Text = "Paste", Id = "3" });
            Items.Add(new CustomItems { Text = "New", Id = "4" });
            return Items;
        }
    }

```

Output be like

![Context Menu Sample](./../images/cm-databinding.png)