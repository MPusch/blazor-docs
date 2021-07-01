# Excel Export

The excel export allows exporting GanttChart data to Excel and CSV formats. You need to use the
 **ExcelExportAsync** and **CsvExportAsync** method for exporting. To enable Excel export in the Gantt chart, set the `AllowExcelExport` property as true.

```csharp
@using Syncfusion.Blazor.Gantt
<SfGantt ID="GanttContainer" @ref="Gantt" AllowExcelExport="true" Toolbar="@(new List<string>() { "ExcelExport", "CsvExport" })" DataSource="@TaskCollection" Height="450px" Width="700px">
    <GanttTaskFields Id="TaskId" Name="TaskName" StartDate="StartDate" EndDate="EndDate" Duration="Duration" Progress="Progress" Dependency="Predecessor" Child="SubTasks"></GanttTaskFields>
    <GanttEvents OnToolbarClick="ToolbarClickHandler" TValue="TaskData"></GanttEvents>
</SfGantt>

@code{
    public SfGantt<TaskData> Gantt;
    public List<TaskData> TaskCollection { get; set; }
    public void ToolbarClickHandler(Syncfusion.Blazor.Navigations.ClickEventArgs args)
    {
        if (args.Item.Id == "GanttContainer_excelexport")
        {
            this.Gantt.ExportToExcelAsync();
        }
        else if (args.Item.Id == "GanttContainer_csvexport")
        {
            this.Gantt.ExportToCsvAsync();
        }
    }
    protected override void OnInitialized()
    {
        this.TaskCollection = GetTaskCollection();
    }

    public class TaskData
    {
        public int TaskId { get; set; }
        public string TaskName { get; set; }
        public DateTime StartDate { get; set; }
        public DateTime EndDate { get; set; }
        public string Duration { get; set; }
        public int Progress { get; set; }
        public string Predecessor { get; set; }
        public List<TaskData> SubTasks { get; set; }
        public int[] ResourceId { get; set; }
    }

    public static List <TaskData> GetTaskCollection() {
        List <TaskData> Tasks = new List <TaskData> () {
            new TaskData() {
                TaskId = 1,
                TaskName = "Project initiation",
                StartDate = new DateTime(2019, 04, 02),
                EndDate = new DateTime(2019, 04, 21),
                SubTasks = (new List <TaskData> () {
                    new TaskData() {
                        TaskId = 2,
                        TaskName = "Identify Site location",
                        StartDate = new DateTime(2019, 04, 02),
                        Duration = "0",
                        Progress = 30
                    },
                    new TaskData() {
                        TaskId = 3,
                        TaskName = "Perform soil test",
                        StartDate = new DateTime(2019, 04, 02),
                        Duration = "4",
                        Predecessor = "2"
                    },
                    new TaskData() {
                        TaskId = 4,
                        TaskName = "Soil test approval",
                        StartDate = new DateTime(2019, 04, 02),
                        Duration = "0",
                        Progress = 30,
                        Predecessor = "3"
                    },
                })
            },
            new TaskData() {
                TaskId = 5,
                TaskName = "Project estimation",
                StartDate = new DateTime(2019, 04, 02),
                EndDate = new DateTime(2019, 04, 21),
                SubTasks = (new List <TaskData> () {
                    new TaskData() {
                        TaskId = 6,
                        TaskName = "Develop floor plan for estimation",
                        StartDate = new DateTime(2019, 04, 04),
                        Duration = "3",
                        Progress = 30,
                        Predecessor = "4"
                    },
                    new TaskData() {
                        TaskId = 7,
                        TaskName = "List materials",
                        StartDate = new DateTime(2019, 04, 04),
                        Duration = "3",
                        Predecessor = "6"
                    },
                    new TaskData() {
                        TaskId = 8,
                        TaskName = "Estimation approval",
                        StartDate = new DateTime(2019, 04, 04),
                        Duration = "0",
                        Predecessor = "7"
                    }
                })
            }
        };
    return Tasks;
}
}
```

## Customize the Excel Export

The excel export provides an option to customize mapping of the gantt chart to excel document.

### Export Hidden Columns

The excel export provides an option to export hidden columns of gantt chart by defining **IncludeHiddenColumn** as **true**.

```csharp
@using Syncfusion.Blazor.Gantt
<SfGantt ID="GanttContainer" @ref="Gantt" AllowExcelExport="true" Toolbar="@(new List<string>() { "ExcelExport", "CsvExport" })" DataSource="@TaskCollection" Height="450px" Width="700px">
    <GanttTaskFields Id="TaskId" Name="TaskName" StartDate="StartDate" EndDate="EndDate" Duration="Duration" Progress="Progress" ParentID="ParentId"></GanttTaskFields>
    <GanttEvents OnToolbarClick="ToolbarClickHandler" TValue="TaskData"></GanttEvents>
    <GanttColumns>
        <GanttColumn Field="TaskId" HeaderText="Task Id" Width="150"></GanttColumn>
        <GanttColumn Field="TaskName" HeaderText="Task Name" Width="250"></GanttColumn>
        <GanttColumn Field="StartDate" HeaderText="StartDate" Width="250" Visible="false"></GanttColumn>
        <GanttColumn Field="Duration" Width="150" HeaderText="Duration" Visible="false"></GanttColumn>
        <GanttColumn Field="Progress" HeaderText="Progress" Width="250"></GanttColumn>
    </GanttColumns>
</SfGantt>

@code{
    public SfGantt<TaskData> Gantt;
    public List<TaskData> TaskCollection { get; set; }
    public void ToolbarClickHandler(Syncfusion.Blazor.Navigations.ClickEventArgs args)
    {
        Syncfusion.Blazor.Grids.ExcelExportProperties ExportProperties = new Syncfusion.Blazor.Grids.ExcelExportProperties();
        ExportProperties.IncludeHiddenColumn = true;
        if (args.Item.Id == "GanttContainer_excelexport")
        {
            this.Gantt.ExportToExcelAsync(ExportProperties);
        }
        else if (args.Item.Id == "GanttContainer_csvexport")
        {
            this.Gantt.ExportToCsvAsync(ExportProperties);
        }
    }
    protected override void OnInitialized()
    {
        this.TaskCollection = GetTaskCollection();
    }

    public class TaskData
    {
        public int TaskId { get; set; }
        public string TaskName { get; set; }
        public DateTime StartDate { get; set; }
        public DateTime EndDate { get; set; }
        public string Duration { get; set; }
        public int Progress { get; set; }
        public int? ParentId { get; set; }
    }

    public static List <TaskData> GetTaskCollection() {
    List <TaskData> Tasks = new List <TaskData> () {

        new TaskData() {
            TaskId = 1,
            TaskName = "Project initiation",
            StartDate = new DateTime(2019, 04, 02),
            EndDate = new DateTime(2019, 04, 21)
        },
        new TaskData() {
            TaskId = 2,
            TaskName = "Identify Site location",
            StartDate = new DateTime(2019, 04, 02),
            Duration = "0",
            Progress = 30,
            ParentId = 1
        },
        new TaskData() {
            TaskId = 3,
            TaskName = "Perform soil test",
            StartDate = new DateTime(2019, 04, 02),
            Duration = "4",
            Progress = 40,
            ParentId = 1
        },
        new TaskData() {
            TaskId = 4,
            TaskName = "Soil test approval",
            StartDate = new DateTime(2019, 04, 02),
            Duration = "0",
            Progress = 30,
            ParentId = 1
        },
        new TaskData() {
            TaskId = 5,
            TaskName = "Project estimation",
            StartDate = new DateTime(2019, 04, 02),
            EndDate = new DateTime(2019, 04, 21)
        },
        new TaskData() {
            TaskId = 6,
            TaskName = "Develop floor plan for estimation",
            StartDate = new DateTime(2019, 04, 04),
            Duration = "3",
            Progress = 30,
            ParentId = 5
        },
        new TaskData() {
            TaskId = 7,
            TaskName = "List materials",
            StartDate = new DateTime(2019, 04, 04),
            Duration = "3",
            Progress = 40,
            ParentId = 5
        },
        new TaskData() {
            TaskId = 8,
            TaskName = "Estimation approval",
            StartDate = new DateTime(2019, 04, 04),
            Duration = "0",
            Progress = 30,
            ParentId = 5
        }
    };
    return Tasks;
}
}
```

### Theme

The Excel export also provides an option to include custom theme for exported Excel document.

To apply theme in exported Excel, define the `Theme` in `ExcelExportProperties`.

```csharp
@using Syncfusion.Blazor.Gantt
<SfGantt ID="GanttContainer" @ref="Gantt" AllowExcelExport="true" Toolbar="@(new List<string>() { "ExcelExport" })" DataSource="@TaskCollection" Height="450px" Width="700px">
    <GanttTaskFields Id="TaskId" Name="TaskName" StartDate="StartDate" EndDate="EndDate" Duration="Duration" Progress="Progress" Dependency="Predecessor" Child="SubTasks"></GanttTaskFields>
    <GanttEvents OnToolbarClick="ToolbarClickHandler" TValue="TaskData"></GanttEvents>
</SfGantt>

@code{
    public SfGantt<TaskData> Gantt;
    public List<TaskData> TaskCollection { get; set; }
    public void ToolbarClickHandler(Syncfusion.Blazor.Navigations.ClickEventArgs args)
    {
        Syncfusion.Blazor.Grids.ExcelExportProperties ExportProperties = new Syncfusion.Blazor.Grids.ExcelExportProperties();
        Syncfusion.Blazor.Grids.ExcelTheme Theme = new Syncfusion.Blazor.Grids.ExcelTheme();

        Syncfusion.Blazor.Grids.ExcelStyle ThemeStyle = new Syncfusion.Blazor.Grids.ExcelStyle()
        {
            FontName = "Segoe UI",
            FontColor = "#666666",
            FontSize = 12
        };

        Theme.Header = ThemeStyle;
        Theme.Record = ThemeStyle;
        ExportProperties.Theme = Theme;
        if (args.Item.Id == "GanttContainer_excelexport")
        {
            this.Gantt.ExportToExcelAsync(ExportProperties);
        }
    }
    protected override void OnInitialized()
    {
        this.TaskCollection = GetTaskCollection();
    }

    public class TaskData
    {
        public int TaskId { get; set; }
        public string TaskName { get; set; }
        public DateTime StartDate { get; set; }
        public DateTime EndDate { get; set; }
        public string Duration { get; set; }
        public int Progress { get; set; }
        public string Predecessor { get; set; }
        public List<TaskData> SubTasks { get; set; }
        public int[] ResourceId { get; set; }
    }

    public static List <TaskData> GetTaskCollection() {
        List <TaskData> Tasks = new List <TaskData> () {
            new TaskData() {
                TaskId = 1,
                TaskName = "Project initiation",
                StartDate = new DateTime(2019, 04, 02),
                EndDate = new DateTime(2019, 04, 21),
                SubTasks = (new List <TaskData> () {
                    new TaskData() {
                        TaskId = 2,
                        TaskName = "Identify Site location",
                        StartDate = new DateTime(2019, 04, 02),
                        Duration = "0",
                        Progress = 30
                    },
                    new TaskData() {
                        TaskId = 3,
                        TaskName = "Perform soil test",
                        StartDate = new DateTime(2019, 04, 02),
                        Duration = "4",
                        Predecessor = "2"
                    },
                    new TaskData() {
                        TaskId = 4,
                        TaskName = "Soil test approval",
                        StartDate = new DateTime(2019, 04, 02),
                        Duration = "0",
                        Progress = 30,
                        Predecessor = "3"
                    },
                })
            },
            new TaskData() {
                TaskId = 5,
                TaskName = "Project estimation",
                StartDate = new DateTime(2019, 04, 02),
                EndDate = new DateTime(2019, 04, 21),
                SubTasks = (new List <TaskData> () {
                    new TaskData() {
                        TaskId = 6,
                        TaskName = "Develop floor plan for estimation",
                        StartDate = new DateTime(2019, 04, 04),
                        Duration = "3",
                        Progress = 30,
                        Predecessor = "4"
                    },
                    new TaskData() {
                        TaskId = 7,
                        TaskName = "List materials",
                        StartDate = new DateTime(2019, 04, 04),
                        Duration = "3",
                        Predecessor = "6"
                    },
                    new TaskData() {
                        TaskId = 8,
                        TaskName = "Estimation approval",
                        StartDate = new DateTime(2019, 04, 04),
                        Duration = "0",
                        Predecessor = "7"
                    }
                })
            }
        };
    return Tasks;
}
}
```

> By default, material theme is applied to the exported Excel document.

### File Name for Exported Document

You can assign the file name for the exported document by defining **FileName** property in excel export properties.

```csharp
@using Syncfusion.Blazor.Gantt
<SfGantt ID="GanttContainer" @ref="Gantt" AllowExcelExport="true" Toolbar="@(new List<string>() { "ExcelExport", "CsvExport" })" DataSource="@TaskCollection" Height="450px" Width="700px">
    <GanttTaskFields Id="TaskId" Name="TaskName" StartDate="StartDate" EndDate="EndDate" Duration="Duration" Progress="Progress" Dependency="Predecessor" Child="SubTasks"></GanttTaskFields>
    <GanttEvents OnToolbarClick="ToolbarClickHandler" TValue="TaskData"></GanttEvents>
</SfGantt>

@code{
    public SfGantt<TaskData> Gantt;
    public List<TaskData> TaskCollection { get; set; }
    public void ToolbarClickHandler(Syncfusion.Blazor.Navigations.ClickEventArgs args)
    {
        if (args.Item.Id == "GanttContainer_excelexport")
        {
            Syncfusion.Blazor.Grids.ExcelExportProperties ExportProperties = new Syncfusion.Blazor.Grids.ExcelExportProperties();
            ExportProperties.FileName = "Gantt.xlsx";
            this.Gantt.ExportToExcelAsync(ExportProperties);
        }
        else if (args.Item.Id == "GanttContainer_csvexport")
        {
            Syncfusion.Blazor.Grids.ExcelExportProperties ExportProperties = new Syncfusion.Blazor.Grids.ExcelExportProperties();
            ExportProperties.FileName = "Gantt.csv";
            this.Gantt.ExportToCsvAsync(ExportProperties);
        }
    }
    protected override void OnInitialized()
    {
        this.TaskCollection = GetTaskCollection();
    }

    public class TaskData
    {
        public int TaskId { get; set; }
        public string TaskName { get; set; }
        public DateTime StartDate { get; set; }
        public DateTime EndDate { get; set; }
        public string Duration { get; set; }
        public int Progress { get; set; }
        public string Predecessor { get; set; }
        public List<TaskData> SubTasks { get; set; }
        public int[] ResourceId { get; set; }
    }

    public static List <TaskData> GetTaskCollection() {
        List <TaskData> Tasks = new List <TaskData> () {
            new TaskData() {
                TaskId = 1,
                TaskName = "Project initiation",
                StartDate = new DateTime(2019, 04, 02),
                EndDate = new DateTime(2019, 04, 21),
                SubTasks = (new List <TaskData> () {
                    new TaskData() {
                        TaskId = 2,
                        TaskName = "Identify Site location",
                        StartDate = new DateTime(2019, 04, 02),
                        Duration = "0",
                        Progress = 30
                    },
                    new TaskData() {
                        TaskId = 3,
                        TaskName = "Perform soil test",
                        StartDate = new DateTime(2019, 04, 02),
                        Duration = "4",
                        Predecessor = "2"
                    },
                    new TaskData() {
                        TaskId = 4,
                        TaskName = "Soil test approval",
                        StartDate = new DateTime(2019, 04, 02),
                        Duration = "0",
                        Progress = 30,
                        Predecessor = "3"
                    },
                })
            },
            new TaskData() {
                TaskId = 5,
                TaskName = "Project estimation",
                StartDate = new DateTime(2019, 04, 02),
                EndDate = new DateTime(2019, 04, 21),
                SubTasks = (new List <TaskData> () {
                    new TaskData() {
                        TaskId = 6,
                        TaskName = "Develop floor plan for estimation",
                        StartDate = new DateTime(2019, 04, 04),
                        Duration = "3",
                        Progress = 30,
                        Predecessor = "4"
                    },
                    new TaskData() {
                        TaskId = 7,
                        TaskName = "List materials",
                        StartDate = new DateTime(2019, 04, 04),
                        Duration = "3",
                        Predecessor = "6"
                    },
                    new TaskData() {
                        TaskId = 8,
                        TaskName = "Estimation approval",
                        StartDate = new DateTime(2019, 04, 04),
                        Duration = "0",
                        Predecessor = "7"
                    }
                })
            }
        };
    return Tasks;
}
}
```

> `Note:` You can refer to our [`Blazor Gantt Chart`](https://www.syncfusion.com/blazor-components/blazor-gantt-chart) feature tour page for its groundbreaking feature representations. You can also explore our [`Blazor Gantt Chart`](https://blazor.syncfusion.com/demos/gantt-chart/default-functionalities?theme=bootstrap4) to knows how to render and configure the gantt.