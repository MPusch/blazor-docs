---
layout: post
title: Positioning in Blazor Diagram Component | Syncfusion
description: Checkout and learn here all about Positioning in Syncfusion Blazor Diagram component and much more details.
platform: Blazor
control: Diagram Component
documentation: ug
---

# How to position node’s port

Diagram allows you to customize the position and appearance of the port efficiently. Port can be aligned relative to the node boundaries. It has Margin, Offset, Horizontal, and Vertical alignment settings. It is quite tricky when all four alignments are used together but gives more control over alignments properties of the [PointPort](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Diagram.PointPort.html) class. Ports of a node can be positioned using the following properties of `PointPort`.

* Offset
* HorizontalAlignment
* VerticalAlignment
* Margin

## Offset

The [Offset](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Diagram.PointPort.html#Syncfusion_Blazor_Diagram_PointPort_Offset) property is used to align the Ports based on fractions. 0 represents top/left corner, 1 represents bottom/right corner, and 0.5 represents half of width/height.

```cshtml
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Nodes="@nodes"/>

@code
{
    DiagramObjectCollection<Node> nodes;

    protected override void OnInitialized()
    {
        nodes = new DiagramObjectCollection<Node>();
        // A node is created and stored in nodes collection.
        Node node = new Node()
        {
            // Position of the node
            OffsetX = 250,
            OffsetY = 250,
            // Size of the node
            Width = 100,
            Height = 100,
            Style = new ShapeStyle() { Fill = "#6495ED", StrokeColor = "white" },
            // Initialize port collection
            Ports = new DiagramObjectCollection<PointPort>()
            {
                new PointPort() 
                {
                    ID = "port1",
                    // Sets the offset for the port
                    Offset = new DiagramPoint() { X = 0, Y = 0.5 },
                    Visibility = PortVisibility.Visible,
                    //Set the style for the port
                    Style= new ShapeStyle() { Fill = "gray", StrokeColor = "black" },
                    Width = 12,
                    Height = 12,
                    // Sets the shape of the port as Square 
                    Shape = PortShapes.Square
                }
            }
        };
        nodes.Add(node);
    }
}
```

![Offset](../images/port_offset.png)

The following table shows the relationship between the shape port position and path port offset (fraction values).

| Offset values | Output |
|---|---|
| (0,0) | ![Left](../images/offset1.png) |
| (0,0.5) | ![Left](../images/offset2.png) |
| (0,1) | ![Left](../images/offset3.png) |
| (0.5,0) | ![Left](../images/offset4.png) |
| (0.5,0.5) | ![Left](../images/offset5.png) |
| (0.5,1) | ![Left](../images/offset6.png) |
| (1,0) | ![Left](../images/offset7.png) |
| (1,0.5) | ![Left](../images/offset8.png) |
| (1,1) | ![Left](../images/offset9.png) |



## Horizontal and Vertical alignment

The [HorizontalAlignment](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Diagram.Port.html#Syncfusion_Blazor_Diagram_Port_HorizontalAlignment) property of the port is used to set how the port is horizontally aligned at the port position determined from the fraction values. The [VerticalAlignment](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Diagram.Port.html#Syncfusion_Blazor_Diagram_Port_VerticalAlignment) property is used to set how the port is vertically aligned at the port position.

The following table shows all the possible alignments visually with `offset (0, 0)`.

| Horizontal Alignment | Vertical Alignment | Output with Offset(0,0) |
| -------- | -------- | -------- |
| Left | Top | ![Left Top Port Alignment](../images/aligment_port1.png) |
| Center | Top | ![Center Top Port Alignment](../images/aligment_port2.png) |
| Right | Top |  ![Right Top Port Alignment](../images/aligment_port3.png) |
| Left | Center | ![Left Center Port Alignment](../images/aligment_port4.png) |
| Center | Center| ![Center Center Port Alignment](../images/aligment_port5.png) |
| Right | Center | ![Right Center Port Alignment](../images/aligment_port6.png) |
| Left | Bottom | ![Left Bottom Port Alignment](../images/aligment_port7.png) |
| Center | Bottom | ![Center Bottom Port Alignment](../images/aligment_port8.png) |
| Right |Bottom |![Right Bottom Port Alignment](../images/aligment_port9.png) |

The following code explains how to align ports.

```cshtml
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Nodes="@nodes"/>

@code
{
    DiagramObjectCollection<Node> nodes;

    protected override void OnInitialized()
    {
        nodes = new DiagramObjectCollection<Node>();
        // A node is created and stored in nodes array.
        Node node = new Node()
        {
            // Position of the node
            OffsetX = 250,
            OffsetY = 250,
            // Size of the node
            Width = 100,
            Height = 100,
            Style = new ShapeStyle() { Fill = "#6495ED", StrokeColor = "white" },
            // Initialize port collection
            Ports = new DiagramObjectCollection<PointPort>() 
            {
                new PointPort() 
                {
                    ID = "port1",
                    Offset = new DiagramPoint() { X = 0, Y = 0 },
                    Visibility = PortVisibility.Visible,
                    //Set the style for the port
                    Style = new ShapeStyle(){ Fill="gray", StrokeColor="black"},
                    Width = 12, 
                    Height = 12, 
                    // Sets the shape of the port as Square                    
                    Shape = PortShapes.Square,
                    HorizontalAlignment = HorizontalAlignment.Center,
                    VerticalAlignment = VerticalAlignment.Center
                }
            }
        };
        nodes.Add(node);
    }
}
```

![Horizontal and Vertical Alignment](../images/HorizontalVerticalaligment.png)


> The value of the `HorizontalAlignment` is `Center` by default. The value of the `VerticalAlignment` is `Center` by default. Alignment positioned based on the offset value.

## Margin

[Margin](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Diagram.Port.html#Syncfusion_Blazor_Diagram_Port_Margin) is an absolute value used to add some blank space to any one of its four sides. The ports can be displaced with the margin property. The following code example explains how to align a port based on its Offset, HorizontalAlignment, VerticalAlignment, and Margin values.

```cshtml
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Nodes="@nodes"/>

@code
{
    DiagramObjectCollection<Node> nodes;

    protected override void OnInitialized()
    {
        nodes = new DiagramObjectCollection<Node>();
        // A node is created and stored in nodes array.
        Node node = new Node()
        {
            // Position of the node
            OffsetX = 250,
            OffsetY = 250,
            // Size of the node
            Width = 100,
            Height = 100,
            Style = new ShapeStyle() { Fill = "#6495ED", StrokeColor = "white" },
            // Initialize port collection
            Ports = new DiagramObjectCollection<PointPort>() 
            {
                new PointPort() 
                {
                    ID = "port1",
                    Offset = new DiagramPoint() { X = 0.5, Y = 1 },
                    Visibility = PortVisibility.Visible,
                    //Set the style for the port
                    Style= new ShapeStyle() { Fill = "gray", StrokeColor = "black" },
                    Width = 12,
                    Height = 12, 
                    // Sets the shape of the port as Square
                    Shape = PortShapes.Square,
                    HorizontalAlignment = HorizontalAlignment.Left,
                    VerticalAlignment = VerticalAlignment.Top,
                    Margin = new Margin() { Top = 10 }
                }
            }
        };
        nodes.Add(node);
    }
}
```

![Margin](../images/port_margin.png)

## See also

* [How to create a node](../nodes/nodes)

* [How to customize the ports](./appearance)

* [How to interact the ports](./interaction)
