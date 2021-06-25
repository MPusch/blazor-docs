---
title: "Data Binding in the Blazor Bullet Chart component | Syncfusion"

component: "Bullet Chart"

description: "Learn here all about the Data Binding of Syncfusion Bullet Chart (SfBulletChart) component and more."
---

# Data Binding in the Blazor Bullet Chart (SfBulletChart)

The [`DataSource`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.SfBulletChart-1.html#Syncfusion_Blazor_Charts_SfBulletChart_1_DataSource) property accepts a collection of values as input that helps to display measures, and compares them to a target bar. To display the actual and the target bar, specify the property from the datasource into the [`ValueField`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.SfBulletChart-1.html#Syncfusion_Blazor_Charts_SfBulletChart_1_ValueField) and the [`TargetField`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.SfBulletChart-1.html#Syncfusion_Blazor_Charts_SfBulletChart_1_TargetField) respectively.

```csharp
@using Syncfusion.Blazor.Charts

<SfBulletChart DataSource="@InputData" ValueField="FieldValue" TargetField="ComparativeMeasureValue" CategoryField="Category" Height="400" Minimum="0" Maximum="20" Interval="5" Title="Profit in %">
    <BulletChartMinorTickLines Width="0"></BulletChartMinorTickLines>
    <BulletChartRangeCollection>
        <BulletChartRange End=5> </BulletChartRange>
        <BulletChartRange End=15></BulletChartRange>
        <BulletChartRange End=20></BulletChartRange>
    </BulletChartRangeCollection>
</SfBulletChart>

@code{
    public class BulletChartData
    {
        public double FieldValue { get; set; }
        public double[] ComparativeMeasureValue { get; set; }
        public string Category { get; set; }
    }
    public List<BulletChartData> InputData = new List<BulletChartData>
    {
        new BulletChartData { FieldValue = 5, ComparativeMeasureValue = new double[] { 7.5 }, Category = "2001" },
        new BulletChartData { FieldValue = 7, ComparativeMeasureValue = new double[] { 5 }, Category = "2002" },
        new BulletChartData { FieldValue = 10, ComparativeMeasureValue = new double[] { 6 }, Category = "2003" },
        new BulletChartData { FieldValue = 5, ComparativeMeasureValue = new double[] { 8 }, Category = "2004" },
        new BulletChartData { FieldValue = 12, ComparativeMeasureValue = new double[] { 5, 6, 9 }, Category = "2005" },
        new BulletChartData { FieldValue = 8, ComparativeMeasureValue = new double[] { 6, 7 }, Category = "2006" }
    };
}
```

![Data Binding in Bullet Chart](images/local-data.png)
