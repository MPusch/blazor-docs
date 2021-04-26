---
title: "Methods in Blazor TreeMap component | Syncfusion"

component: "TreeMap"

description: "Learn here all about Methods of Syncfusion TreeMap (SfTreeMap) component and more."
---

# Methods in Blazor TreeMap (SfTreeMap)

Create an object for the TreeMap component using `@ref` property and call the desired TreeMap method.

## Print

To print the rendered TreeMap component by setting the [`AllowPrint`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.TreeMap.SfTreeMap-1.html#Syncfusion_Blazor_TreeMap_SfTreeMap_1_AllowPrint) property to **true**.

```csharp
@using Syncfusion.Blazor.TreeMap;

<button @onclick="PrintMap">Print Treemap</button>
<SfTreeMap @ref="Treemap" DataSource="@growthReport" WeightValuePath="GDP" TValue="Country" AllowPrint="true">
    <TreeMapLeafItemSettings LabelPath="Name" Fill="lightgray">
    </TreeMapLeafItemSettings>
</SfTreeMap>

@code {
    public SfTreeMap<Country> Treemap { get; set; }
    public async Task PrintMap()
    {
        await Treemap.Print();
    }
    public class Country
    {
        public string Name { get; set; }
        public double GDP { get; set; }
    }
    public List<Country> growthReport = new List<Country> {
        new Country  {Name="United States", GDP=17946 },
        new Country  {Name="China", GDP=10866 },
        new Country  {Name="Japan", GDP=4123 },
    };
}
```

## Export

Export the current TreeMap component to different file formats such as [`PNG`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.TreeMap.ExportType.html#Syncfusion_Blazor_TreeMap_ExportType_PNG), [`PDF`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.TreeMap.ExportType.html#Syncfusion_Blazor_TreeMap_ExportType_PDF), [`JPEG`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.TreeMap.ExportType.html#Syncfusion_Blazor_TreeMap_ExportType_JPEG) and [`SVG`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.TreeMap.ExportType.html#Syncfusion_Blazor_TreeMap_ExportType_SVG).

[`AllowImageExport`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.TreeMap.SfTreeMap-1.html#Syncfusion_Blazor_TreeMap_SfTreeMap_1_AllowImageExport) and [`AllowPdfExport`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.TreeMap.SfTreeMap-1.html#Syncfusion_Blazor_TreeMap_SfTreeMap_1_AllowPdfExport) property represents to allow the file to be download in image and pdf type export.

|   Arguments      |   Description                                       |
|----------------------| ----------------------------------------------------|
|     type             |    Define the export type such as **PNG**, **PDF**, **JPEG** and **SVG**.   |
|     fileName        |    Define the file name.                             |
|     orientation      |    Define the orientation such as **horizontal** and **vertical**.     |
| allowDownload | Define the export file to be download or not. |

> Export method returns the **Base64** string, if **allowDownload** argument is set to **false**. The file can be download by paste the returned **Base64** string in the browser URL bar and press the enter button.

```csharp
@using Syncfusion.Blazor.TreeMap;

<button @onclick="ExportMap">Export Treemap</button>
<SfTreeMap @ref="Treemap" DataSource="@growthReport" WeightValuePath="GDP" TValue="Country" AllowImageExport="true" AllowPdfExport="true">
    <TreeMapLeafItemSettings LabelPath="Name" Fill="lightgray">
    </TreeMapLeafItemSettings>
</SfTreeMap>

@code {
    public SfTreeMap<Country> Treemap { get; set; }
    public async Task ExportMap()
    {
        await Treemap.Export(ExportType.SVG, "Export", Syncfusion.PdfExport.PdfPageOrientation.Portrait, true);
    }
    public class Country
    {
        public string Name { get; set; }
        public double GDP { get; set; }
    }
    private List<Country> growthReport = new List<Country> {
        new Country  {Name="United States", GDP=17946 },
        new Country  {Name="China", GDP=10866 },
        new Country  {Name="Japan", GDP=4123 },
    };
}
```

## Refresh

The TreeMap component is rendered again.

```csharp
@using Syncfusion.Blazor.TreeMap;

<button @onclick="RefreshCall">Refresh</button>
<SfTreeMap @ref="Treemap" DataSource="@growthReport" WeightValuePath="GDP" TValue="Country" AllowImageExport="true" AllowPdfExport="true">
</SfTreeMap>

@code {
    public SfTreeMap<Country> Treemap { get; set; }
    public async Task RefreshCall()
    {
        await Treemap.Refresh();
    }
    public class Country
    {
        public string Name { get; set; }
        public double GDP { get; set; }
    }
    private List<Country> growthReport = new List<Country> {
        new Country  {Name="United States", GDP=17946 },
        new Country  {Name="China", GDP=10866 },
        new Country  {Name="Japan", GDP=4123 },
    };
}
```

## SelectItem

Select or unselect of the TreeMap item can be achieved by programmatically using [`SelectItem`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.TreeMap.SfTreeMap-1.html#Syncfusion_Blazor_TreeMap_SfTreeMap_1_SelectItem_System_String___System_Boolean_) method.  

|   Arguments      |   Description                                       |
|----------------------| ----------------------------------------------------|
| levelOrder | Define the level order name for the treemap item. |
| isSelected | Define whether it to be select or unselect. |

```csharp
@using Syncfusion.Blazor.TreeMap;

<button @onclick="SelectCall">Select</button>
<SfTreeMap @ref="Treemap" DataSource="@growthReport" WeightValuePath="GDP" TValue="Country">
    <TreeMapLeafItemSettings LabelPath="Name" Fill="lightgray">
    </TreeMapLeafItemSettings>
    <TreeMapSelectionSettings Enable="true" Fill="#a4d1f2">
    </TreeMapSelectionSettings>
</SfTreeMap>

@code {
    public SfTreeMap<Country> Treemap { get; set; }
    public async Task SelectCall()
    {
        await Treemap.SelectItem(new string[] { "United States" }, true);
    }
    public class Country
    {
        public string Name { get; set; }
        public double GDP { get; set; }
    }
    private List<Country> growthReport = new List<Country> {
        new Country  {Name="United States", GDP=17946 },
        new Country  {Name="China", GDP=10866 },
        new Country  {Name="Japan", GDP=4123 },
    };
}
```
