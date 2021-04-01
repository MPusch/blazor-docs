<!-- markdownlint-disable MD036 -->

# Mark a threshold in chart

You can mark a threshold in chart by using the [`ChartStripline`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.AxisModel.html#Syncfusion_Blazor_Charts_AxisModel_StripLines).

To mark a threshold in chart, follow the given steps:

**Step 1**:

By using the [`Start`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.ChartCommonStripLines.html#Syncfusion_Blazor_Charts_ChartCommonStripLines_Start) and [`End`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.ChartCommonStripLines.html#Syncfusion_Blazor_Charts_ChartCommonStripLines_End) properties of [`ChartStripline`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.AxisModel.html#Syncfusion_Blazor_Charts_AxisModel_StripLines) in vertical axis, you can mark the threshold
for y values of the data.

```razor
 <ChartPrimaryYAxis>
        <ChartStripLines>
            <ChartStripline Start="30" End="30.1" Color="red"></ChartStripline>
        </ChartStripLines>
  </ChartPrimaryYAxis>

  ```

{% aspTab template="chart/how-to/threshold", sourceFiles="threshold.razor" %}

{% endaspTab %}

> Note: You can refer to our [`Blazor Charts`](https://www.syncfusion.com/blazor-components/blazor-charts) feature tour page for its groundbreaking feature representations. You can also explore our [`Blazor Chart example`](https://blazor.syncfusion.com/demos/chart/line?theme=bootstrap4) to knows various chart types and how to represent time-dependent data, showing trends in data at equal intervals.