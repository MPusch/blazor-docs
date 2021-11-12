---
layout: post
title: Getting Started with Blazor CheckBox Component | Syncfusion
description: Checkout and learn more details about getting started with the Blazor CheckBox component of Syncfusion.
platform: Blazor
control: Checkbox
documentation: ug
---

<!-- markdownlint-disable MD024 -->

# Getting Started with Blazor CheckBox Component

This section briefly explains about how to include [Checkbox](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Buttons.SfCheckBox-1.html) Component in your Blazor server-side application. You can refer [Getting Started with Syncfusion Blazor for Server-side in Visual Studio](https://blazor.syncfusion.com/documentation/getting-started/blazor-server-side-visual-studio/) page for the introduction and configuring the common specifications.

To get started quickly with the CheckBox Component using Blazor, you can check out this video:

{% youtube
"youtube:https://www.youtube.com/watch?v=a6HR1QGAvLo"%}

## Importing Syncfusion Blazor component in the application

1. Install the [Syncfusion.Blazor](https://www.nuget.org/packages/Syncfusion.Blazor) NuGet package to the application by using the `NuGet Package Manager`.

2. You can add the client-side style resources through [CDN](https://blazor.syncfusion.com/documentation/appearance/themes#cdn-reference) or from [NuGet](https://blazor.syncfusion.com/documentation/appearance/themes#static-web-assets) package in the `<head>` element of the `~/Pages/_Host.cshtml` page.

```html
<head>
    <link href="_content/Syncfusion.Blazor/styles/bootstrap4.css" rel="stylesheet" />
    @*<link href="https://cdn.syncfusion.com/blazor/{{ site.blazorversion }}/styles/bootstrap4.css" rel="stylesheet" />*@
</head>
```

For Internet Explorer 11 kindly refer the polyfills. Refer the [documentation](https://blazor.syncfusion.com/documentation/common/how-to/render-blazor-server-app-in-ie/) for more information.

```html
<head>
    <link href="_content/Syncfusion.Blazor/styles/bootstrap4.css" rel="stylesheet" />
    <script src="https://github.com/Daddoon/Blazor.Polyfill/releases/download/3.0.1/blazor.polyfill.min.js"></script>
</head>
```

## Adding component package to the application

Open `/_Imports.razor file` and import the **Syncfusion.Blazor.Buttons** package.

```csharp

@using Syncfusion.Blazor.Buttons

```

## Add SyncfusionBlazor service in Startup.cs

Open the **Startup.cs** file and add services required by Syncfusion components.
Add **services.AddSyncfusionBlazor()** method in the ConfigureServices function as follows.

```csharp
namespace BlazorApplication
{
    public class Startup
    {
        ....
        ....
        public void ConfigureServices(IServiceCollection services)
        {
            ....
            ....
            services.AddSyncfusionBlazor();
        }
    }
}
```

> To enable custom client side resource loading from CRG or CDN, you need to disable resource loading by **AddSyncfusionBlazor(true)** and load the scripts in the HEAD element of the **~/Pages/_Host.cshtml** page.

```html
<head>
    <environment include="Development">
        <script src="https://cdn.syncfusion.com/blazor/{{ site.blazorversion }}/syncfusion-blazor.min.js">
        </script>
    </environment>
</head>
```

## Adding component package to the application

Open `/_Imports.razor file` and import the Syncfusion.Blazor.Buttons packages. Otherwise, import these packages in the individual `razor` pages.

```cshtml
@using Syncfusion.Blazor
@using Syncfusion.Blazor.Buttons
```

## Adding Checkbox component to the application

Now, add the Syncfusion Blazor Checkbox component in `razor` page in the `Pages` folder. For example, the Checkbox component is added in the `~/Pages/Index.razor` page.

```cshtml
<SfCheckBox Label="Default" @bind-Checked="isChecked"></SfCheckBox>

@code 
{
    private bool isChecked = true;
}
```

## Run the application

After successful compilation of your application, simply press F5 to run the application. The Blazor Checkbox component will render in the web browser as shown below

![Blazor CheckBox Component](./images/blazor-checkbox-component.png)

## See Also

* [Getting Started with Syncfusion Blazor for Client-Side in .NET Core CLI](https://blazor.syncfusion.com/documentation/getting-started/blazor-webassembly-dotnet-cli/)
* [Getting Started with Syncfusion Blazor for Server-Side in Visual Studio](https://blazor.syncfusion.com/documentation/getting-started/blazor-server-side-visual-studio/)
* [Getting Started with Syncfusion Blazor for Server-Side in .NET Core CLI](https://blazor.syncfusion.com/documentation/getting-started/blazor-server-side-dotnet-cli/)