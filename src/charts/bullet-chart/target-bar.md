---
title: "Target Bar in the Blazor Bullet Chart component | Syncfusion"

component: "Bullet Chart"

description: "Learn here all about the Target Bar of Syncfusion Bullet Chart (SfBulletChart) component and more."
---

# Target Bar in the Blazor Bullet Chart (SfBulletChart)

The line marker that runs perpendicular to the orientation of the graph is known as the **Comparative Measure** and it is used as a target marker to compare against the feature measure value. This is also called as the **Target Bar** in the Bullet Chart. To display the target bar, the [`TargetField`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.SfBulletChart-1.html#Syncfusion_Blazor_Charts_SfBulletChart_1_TargetField) should be mapped to the appropriate field from the datasource.

```csharp
@using Syncfusion.Blazor.Charts

<SfBulletChart DataSource="@BulletChartData" TargetField="Target" Minimum="0" Maximum="30" Interval="5">
    <BulletChartRangeCollection>
        <BulletChartRange End=20> </BulletChartRange>
        <BulletChartRange End=25></BulletChartRange>
        <BulletChartRange End=30></BulletChartRange>
    </BulletChartRangeCollection>
</SfBulletChart>

@code{
    public class ChartData
    {
        public double Target { get; set; }
    }
    public List<ChartData> BulletChartData = new List<ChartData>
    {
        new ChartData { Target = 25 }
    };
}
```

![Target Bar in Bullet Chart](images/target-bar.png)

## Types of Target Bar

The shape of the target bar can be customized using the [`TargetTypes`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.SfBulletChart-1.html#Syncfusion_Blazor_Charts_SfBulletChart_1_TargetTypes) property and it supports [`Circle`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.TargetType.html#Syncfusion_Blazor_Charts_TargetType_Circle), [`Cross`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.TargetType.html#Syncfusion_Blazor_Charts_TargetType_Cross), and [`Rect`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.TargetType.html#Syncfusion_Blazor_Charts_TargetType_Rect) shapes. The default type of the target bar is [`Rect`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.TargetType.html#Syncfusion_Blazor_Charts_TargetType_Rect).

```csharp
@using Syncfusion.Blazor.Charts

<SfBulletChart DataSource="@BulletChartData" TargetField="Target" Minimum="0" Maximum="30" Interval="5" TargetTypes="new List<TargetType>() { TargetType.Cross }">
    <BulletChartRangeCollection>
        <BulletChartRange End=20> </BulletChartRange>
        <BulletChartRange End=25></BulletChartRange>
        <BulletChartRange End=30></BulletChartRange>
    </BulletChartRangeCollection>
</SfBulletChart>
```

> Refer to the [code block](#target-bar) to know about the property value of the **BulletChartData**.

![Target Bar with types](images/target-type.png)

## Target Bar Customization

The following properties can be used to customize the Target Bar.

* [`TargetColor`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.SfBulletChart-1.html#Syncfusion_Blazor_Charts_SfBulletChart_1_TargetColor) - Specifies the fill color of the Target Bar.
* [`TargetWidth`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.SfBulletChart-1.html#Syncfusion_Blazor_Charts_SfBulletChart_1_TargetWidth) - Specifies the width of the Target Bar.

```csharp
@using Syncfusion.Blazor.Charts

<SfBulletChart DataSource="@BulletChartData" TargetField="Target" Minimum="0" Maximum="30" Interval="5" TargetColor="red" TargetWidth="10">
    <BulletChartRangeCollection>
        <BulletChartRange End=20> </BulletChartRange>
        <BulletChartRange End=25></BulletChartRange>
        <BulletChartRange End=30></BulletChartRange>
    </BulletChartRangeCollection>
</SfBulletChart>
```

> Refer to the [code block](#target-bar) to know about the property value of the **BulletChartData**.

![Target Bar with customization](images/target-custom.png)
