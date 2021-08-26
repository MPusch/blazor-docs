---
layout: post
title: Icons Library in Blazor - Syncfusion
description: Learn here all about that how to using Icons in the Syncfusion Blazor Component and its type of icons.
platform: Blazor
component: Common
documentation: ug
---

# Blazor Icons Library

The Syncfusion Blazor library provides the set of `base64` formatted font icons which are being used in the Syncfusion Blazor components. These can be utilized in the web application also as needed.

## Steps to use Icon

1. Add a class `e-icons` to the HTML element that shows the icon. This class contains the font-family and common property of the font icons.

2. Add the icon class with corresponding icon content from the [available icons](#available-icons). For example, the following code snippet represents the search icon class.

    ```css
    .e-search:before{
        content:'\e993';
    }
    ```

3. Add `e-icons` and `e-search` class to the HTML element.

    ```html
    <span class="e-icons e-search"></span>
    ```

4. Add the client-side resources through CDN in the `<head>` element of the `~/wwwroot/index.html` in Blazor WebAssembly app or `~/Pages/_Host.cshtml` in Blazor server app.

    ```html
    <head>
        <link href="https://cdn.syncfusion.com/blazor/{{ site.blazorversion }}/bootstrap4.css" rel="stylesheet" />
    </head>
    ```

    The following code snippet represents the complete example of icon usage in `~/Pages/Index.razor`.

    ```cshtml
        <div class="icons">
            <ul>
                <li><span class="e-icons e-search"></span></li>
                <li><span class="e-icons e-upload"></span></li>
                <li><span class="e-icons e-font"></span></li>
            </ul>
        </div>
        <style>
            .e-search:before{
                content:'\e993';
            }
            .e-upload:before{
                content: '\e725';
            }
            .e-font:before{
                content: '\e34c';
            }
        </style>
    ```

## Customize Icon

The Syncfusion Blazor icon library can customize its color and size by overriding the `e-icons` class.

```cshtml
    <style>
        .e-icons{
            color: #00ffff;
            font-size: 26px;
        }
        .e-search:before{
            content: '\e993';
        }
        .e-upload:before{
            content: '\e725';
        }
        .e-font:before{
            content: '\e34c';
        }
    </style>
    <div class="icons">
        <ul>
            <li><span class="e-icons e-search"></span></li>
            <li><span class="e-icons e-upload"></span></li>
            <li><span class="e-icons e-font"></span></li>
            </ul>
    </div>
```

## Available Icons

The complete pack of Syncfusion Blazor icons is listed in the following table. The corresponding icon content can be referred to the content section.

<!-- markdownlint-disable MD033 -->

### Bootstrap 4

<iframe class="doc-sample-frame" src="https://ej2.syncfusion.com/products/icons/bootstrap4/demo.html" style="height:1000px;width:100%;"></iframe>

### Bootstrap

<iframe class="doc-sample-frame" src="https://ej2.syncfusion.com/products/icons/bootstrap/demo.html" style="height:1000px;width:100%;"></iframe>

### Material

<iframe class="doc-sample-frame" src="https://ej2.syncfusion.com/products/icons/material/demo.html" style="height:1000px;width:100%;"></iframe>

### Office Fabric

<iframe class="doc-sample-frame" src="https://ej2.syncfusion.com/products/icons/fabric/demo.html" style="height:1000px;width:100%;"></iframe>

### High Contrast

<iframe class="doc-sample-frame" src="https://ej2.syncfusion.com/products/icons/highcontrast/demo.html" style="height:1000px;width:100%;"></iframe>

### Tailwind CSS

<iframe class="doc-sample-frame" src="https://ej2.syncfusion.com/products/icons/tailwind/demo.html" style="height:1000px;width:100%;"></iframe>
