---
title: "Headers and Footers"
component: "Word processor"
description: "Learn header footer support in Blazor Word processor and how to work with it."
---

# Headers and Footers

[`Blazor Document Editor`](https://www.syncfusion.com/blazor-components/blazor-word-processor) supports headers and footers in its document. Each section in the document can have the following types of headers and footers:

* First page: Used only on the first page of the section.
* Even pages: Used on all even numbered pages in the section.
* Default: Used on all pages of the section, where first or even pages are not applicable or not specified.

You can define this by setting format properties of the corresponding section using the following sample code.

```csharp
//Defines whether different header footer is required for first page of the section
documentEditor.Selection.SectionFormat.SetDifferentFirstPage(true);
//Defines whether different header footer is required for odd and even pages in the section
documentEditor.Selection.SectionFormat.SetDifferentOddAndEvenPages(true);
```

## Go to header footer region

Double click in header or footer region to move the selection into it. You can also do this by using the following code.

```csharp
documentEditor.Selection.GoToHeader();
```

```csharp
documentEditor.Selection.GoToFooter();
```

## Header and footer distance

You can define the distance of header region content from the top of the page. Refer to the following sample code.

```csharp
documentEditor.Selection.SectionFormat.SetHeaderDistance(36);
```

Same way, you can define the distance of footer region content from the bottom of the page. Refer to the following sample code.

```csharp
documentEditor.Selection.SectionFormat.SetFooterDistance(36);
```

## Close header footer region

Move the selection to the document body from header or footer region by double clicking or tapping the document area. You can also perform this by using the following sample code.

```csharp
documentEditor.Selection.CloseHeaderFooter();
```

You can also explore our [`Blazor Word Processor`](https://blazor.syncfusion.com/demos/document-editor/default-functionalities) example to know how to render and configure the document editor.