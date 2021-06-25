---
title: "Title and SubTitle in Blazor Bullet Chart component | Syncfusion"

component: "Bullet Chart"

description: "Learn here all about Title and SubTitle of Syncfusion Bullet Chart (SfBulletChart) component and more."
---

# Title and SubTitle in Blazor Bullet Chart (SfBulletChart)

## Title

The title of the Bullet Chart displays the information about the data plotted by specifying it in the [`Title`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.SfBulletChart-1.html#Syncfusion_Blazor_Charts_SfBulletChart_1_Title) property.

```csharp
@using Syncfusion.Blazor.Charts

<SfBulletChart DataSource="@BulletChartData" Title="Sales Rate" ValueField="FieldValue" TargetField="TargetValue" Minimum="0" Maximum="100" Interval="20">
    <BulletChartRangeCollection>
        <BulletChartRange End=35> </BulletChartRange>
        <BulletChartRange End=50></BulletChartRange>
        <BulletChartRange End=100></BulletChartRange>
    </BulletChartRangeCollection>
</SfBulletChart>

@code{
    public class ChartData
    {
        public double FieldValue { get; set; }
        public double TargetValue { get; set; }
    }
    public List<ChartData> BulletChartData = new List<ChartData>
    {
        new ChartData { FieldValue = 55, TargetValue = 75 }
    };
}
```

![Title in Bullet Chart](images/default-title.png)

## Subtitle

To show additional information about the data plotted, the Bullet Chart can also be given a subtitle using the [`Subtitle`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.SfBulletChart-1.html#Syncfusion_Blazor_Charts_SfBulletChart_1_Subtitle) property.

```csharp
@using Syncfusion.Blazor.Charts

<SfBulletChart DataSource="@BulletChartData" Height="150px" Subtitle="(in dollars $)" Title="Sales Rate" ValueField="FieldValue" TargetField="TargetValue" Minimum="0" Maximum="100" Interval="20">
    <BulletChartRangeCollection>
        <BulletChartRange End=35> </BulletChartRange>
        <BulletChartRange End=50></BulletChartRange>
        <BulletChartRange End=100></BulletChartRange>
    </BulletChartRangeCollection>
</SfBulletChart>
```

> Refer to the [code block](#title) to know about the property value of the **BulletChartData**.

![Subtitle in Bullet Chart](images/sub-title.png)

## Title and Subtitle Position

The title and the subtitle positions can be customized using the [`TitlePosition`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.SfBulletChart-1.html#Syncfusion_Blazor_Charts_SfBulletChart_1_TitlePosition) property. Possible positions are [`Left`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.TextPosition.html#Syncfusion_Blazor_Charts_TextPosition_Left), [`Right`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.TextPosition.html#Syncfusion_Blazor_Charts_TextPosition_Right), [`Top`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.TextPosition.html#Syncfusion_Blazor_Charts_TextPosition_Top) and [`Bottom`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.TextPosition.html#Syncfusion_Blazor_Charts_TextPosition_Bottom).

```csharp
@using Syncfusion.Blazor.Charts

<SfBulletChart DataSource="@BulletChartData" TitlePosition="TextPosition.Left" Height="100px" Subtitle="(in dollars $)" Title="Sales Rate" ValueField="FieldValue" TargetField="TargetValue" Minimum="0" Maximum="100" Interval="20">
    <BulletChartRangeCollection>
        <BulletChartRange End=35> </BulletChartRange>
        <BulletChartRange End=50></BulletChartRange>
        <BulletChartRange End=100></BulletChartRange>
    </BulletChartRangeCollection>
</SfBulletChart>

<SfBulletChart DataSource="@BulletChartData" TitlePosition="TextPosition.Right" Height="100px" Subtitle="(in dollars $)" Title="Sales Rate" ValueField="FieldValue" TargetField="TargetValue" Minimum="0" Maximum="100" Interval="20">
    <BulletChartRangeCollection>
        <BulletChartRange End=35> </BulletChartRange>
        <BulletChartRange End=50></BulletChartRange>
        <BulletChartRange End=100></BulletChartRange>
    </BulletChartRangeCollection>
</SfBulletChart>

<SfBulletChart DataSource="@BulletChartData" TitlePosition="TextPosition.Top" Height="150px" Subtitle="(in dollars $)" Title="Sales Rate" ValueField="FieldValue" TargetField="TargetValue" Minimum="0" Maximum="100" Interval="20">
    <BulletChartRangeCollection>
        <BulletChartRange End=35> </BulletChartRange>
        <BulletChartRange End=50></BulletChartRange>
        <BulletChartRange End=100></BulletChartRange>
    </BulletChartRangeCollection>
</SfBulletChart>

<SfBulletChart DataSource="@BulletChartData" TitlePosition="TextPosition.Bottom" Height="150px" Subtitle="(in dollars $)" Title="Sales Rate" ValueField="FieldValue" TargetField="TargetValue" Minimum="0" Maximum="100" Interval="20">
    <BulletChartRangeCollection>
        <BulletChartRange End=35> </BulletChartRange>
        <BulletChartRange End=50></BulletChartRange>
        <BulletChartRange End=100></BulletChartRange>
    </BulletChartRangeCollection>
</SfBulletChart>
```

> Refer to the [code block](#title) to know about the property value of the **BulletChartData**.

![Title and Subtitle Position](images/title-positions.png)

## Title and Subtitle Customization

The title and the subtitle - color, opacity, font size, font family, font weight, and font style can be customized using the [`BulletChartTitleStyle`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.BulletChartTitleStyle.html) and the [`BulletChartSubTitleStyle`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.BulletChartSubTitleStyle.html) settings. The [`MaximumTitleWidth`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.BulletChartCommonFont.html#Syncfusion_Blazor_Charts_BulletChartCommonFont_MaximumTitleWidth) property determinates the maximum width of the text, and the [`TextOverflow`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.BulletChartCommonFont.html#Syncfusion_Blazor_Charts_BulletChartCommonFont_TextOverflow) property is used to [`Wrap`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.TextOverflow.html#Syncfusion_Blazor_Charts_TextOverflow_Wrap) or [`Trim`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.TextOverflow.html#Syncfusion_Blazor_Charts_TextOverflow_Trim) the title and the subtitle, when the text size exceeds the [`MaximumTitleWidth`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.BulletChartCommonFont.html#Syncfusion_Blazor_Charts_BulletChartCommonFont_MaximumTitleWidth). The default value of the [`TextOverflow`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.BulletChartCommonFont.html#Syncfusion_Blazor_Charts_BulletChartCommonFont_TextOverflow) is [`None`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.TextOverflow.html#Syncfusion_Blazor_Charts_TextOverflow_None).

```csharp
@using Syncfusion.Blazor.Charts

<SfBulletChart DataSource="@BulletChartData" Height="150px" Title="Sales Rate" Subtitle="(in dollars $)" ValueField="FieldValue" TargetField="TargetValue" Minimum="0" Maximum="100" Interval="20">
    <BulletChartTitleStyle Color="red" Opacity="1" Size="15px"></BulletChartTitleStyle>
    <BulletChartSubTitleStyle Color="red" Opacity="0.5" Size="13px" FontStyle="italic" MaximumTitleWidth="70" TextOverflow="TextOverflow.Trim"></BulletChartSubTitleStyle>
    <BulletChartRangeCollection>
        <BulletChartRange End=35> </BulletChartRange>
        <BulletChartRange End=50></BulletChartRange>
        <BulletChartRange End=100></BulletChartRange>
    </BulletChartRangeCollection>
</SfBulletChart>
```

> Refer to the [code block](#title) to know about the property value of the **BulletChartData**.

![Title and Subtitle Customization](images/title-custom.png)
