---
layout: post
title: Create custom Grid component in Blazor DataGrid Component | Syncfusion
description: Checkout and learn here all about Create custom Grid component in Syncfusion Blazor DataGrid component and more.
platform: Blazor
control: DataGrid
documentation: ug
---

# Create custom Grid component in Blazor DataGrid Component

You can create a custom Grid component by rendering the SfGrid as a new razor component. It helps to create your own custom component when you might want to create multiple grids with same configuration or with default configuration through out your application.

This is demonstrated in below example by create a custom Grid component called CustomGrid, where we have rendered SfGrid with some basic default properties such as GridPageSettings etc. which will be reflected in all the Grids rendered using CustomGrid component.

CustomGrid.razor

```cshtml
@using Syncfusion.Blazor.Grids
@typeparam TValue
@inherits SfGrid<TValue>

<SfGrid TValue="TValue" AllowSorting="AllowSorting" AllowPaging="AllowPaging" @attributes="props">
    @ChildContent
    <GridPageSettings PageCount="PAGE_COUNT" PageSize="DEFAULT_PAGE_SIZE" PageSizes="PageSizes"></GridPageSettings>
</SfGrid>
```

CustomGrid.razor.cs

```csharp
using Microsoft.AspNetCore.Components;
using Syncfusion.Blazor.Grids;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace SF_Grid_Inheritance.Shared
{
    public partial class CustomGrid<TValue> : SfGrid<TValue>
    {
        public const int PAGE_COUNT = 5;
        public const int DEFAULT_PAGE_SIZE = 10;
        public string[] PageSizes = new string[] { "10", "20", "50" };
        IReadOnlyDictionary<string, object> props { get; set; }
        public override Task SetParametersAsync(ParameterView parameters)
        {
            //assign the additional parameters
            props = parameters.ToDictionary();
            return base.SetParametersAsync(parameters);
        }
        protected async override Task OnParametersSetAsync()
        {
            AllowPaging = true;
            AllowSorting = true;
            await base.OnParametersSetAsync();
        }
    }
}
```

Index.razor

```csharp

<CustomGrid DataSource="Orders" TValue="Order"></CustomGrid>

@code{
    public List<Order> Orders { get; set; }
    protected override void OnInitialized()
    {
        Orders = Enumerable.Range(1, 75).Select(x => new Order()
        {
            OrderID = 1000 + x,
            CustomerID = (new string[] { "ALFKI", "ANANTR", "ANTON", "BLONP", "BOLID" })[new Random().Next(5)],
            Freight = 2.1 * x,
            OrderDate = DateTime.Now.AddDays(-x),
        }).ToList();
    }
    public class Order
    {
        public int? OrderID { get; set; }
        public string CustomerID { get; set; }
        public DateTime? OrderDate { get; set; }
        public double? Freight { get; set; }
    }
}
```