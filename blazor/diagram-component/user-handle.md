---
layout: post
title: User Handle in Blazor Diagram Component | Syncfusion
description: Learn here all about how to create the user handles in Syncfusion Blazor Diagram component and more.
platform: Blazor
control: Diagram Component
documentation: ug
---

# User Handles for node , connector in Blazor Diagram Component

User handles are customizable handles that can be used to perform custom actions and default clipboard actions.

## Initialization an user handle

The user handle can enables for the selected nodes/connectors by setting a `SelectorConstraints` as `UserHandles` and then use the `UserHandle` class to create an object for the user handles. The following code example used to enable and create an user handles for the diagram nodes/connectors.

```cshtml
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px"
                    Nodes="@NodeCollection"
                    SelectedItems="@SelectedModel">
    <SnapSettings>
        <HorizontalGridLines LineColor="White" LineDashArray="2,2" />
        <VerticalGridLines LineColor="White" LineDashArray="2,2" />
    </SnapSettings>
</SfDiagramComponent>

@code
{
    // Defines diagram's nodes collection
    DiagramObjectCollection<Node> nodes = new DiagramObjectCollection<Node>();
    // Defines diagram's SelectedItems
    Selector SelectedModel = new Selector();
    DiagramObjectCollection<UserHandle> UserHandles = new DiagramObjectCollection<UserHandle>();
    protected override void OnInitialized()
    {
        //Creating the userhandle for cloning the objects
        UserHandle cloneHandle = new UserHandle()
        {
            //Name of the user handle
            Name = "clone",
            //Set pathdata for userhandle
            PathData = "M60.3,18H27.5c-3,0-5.5,2.4-5.5,5.5v38.2h5.5V23.5h32.7V18z M68.5,28.9h-30c-3,0-5.5,2.4-5.5,5.5v38.2c0,3,2.4,5.5,5.5,5.5h30c3,0,5.5-2.4,5.5-5.5V34.4C73.9,31.4,71.5,28.9,68.5,28.9z M68.5,72.5h-30V34.4h30V72.5z",
            //Set visibility for the user handle
            Visible = true,
            //Set the position for the user handle
            Offset = 0,
            //Set side based on the given offset
            Side = Side.Bottom,
            //set margin for the user handle
            Margin = new Margin() { Top = 0, Bottom = 0, Left = 0, Right = 0 }
        };
        //Add user handle to the collection...
        UserHandles = new DiagramObjectCollection<UserHandle>()
        {
            cloneHandle
        };
        SelectedModel = new Selector()
        {
            //Enable userhandle for selected items...
            Constraints = SelectorConstraints.UserHandle,
            UserHandles = this.UserHandles
        };
        nodes = new DiagramObjectCollection<Node>();
        Node diagramNode = new Node()
        {
            ID = "node1",
            OffsetX = 100,
            OffsetY = 100,
            Width = 100,
            Height = 100,
            Style = new ShapeStyle() { Fill = "#6495ED", StrokeColor = "none" },
            Annotations = new DiagramObjectCollection<ShapeAnnotation>() { new ShapeAnnotation { Content = "Node" } }
        };
        nodes.Add(diagramNode);
    }
}
```

![User handle for node in blazor diagram](images/userhandle1.png)

## Customization

### Position

The `Offset` property of user handle is used to align the user handles based on fractions. 0 represents Top-Left corner, 1 represents Bottom-Right corner, and 0.5 represents half of Width or Height. The `Side` property is used to set how the user handle is aligned based on the given `Offset`.

The following table shows all the possible alignments visually shows the user handle positions.

| Offset | Side | Output |
| -------- | -------- | -------- |
|0|Left|![User handle for node in blazor diagram](images/userhandle2.png)|
|0|Right|![User handle for node in blazor diagram](images/userhandle3.png)|
|0|Top|![User handle for node in blazor diagram](images/userhandle4.png)|
|0|Bottom|![User handle for node in blazor diagram](images/userhandle5.png)|
|1|Left|![User handle for node in blazor diagram](images/userhandle6.png)|
|1|Right|![User handle for node in blazor diagram](images/userhandle7.png)|
|1|Top|![User handle for node in blazor diagram](images/userhandle8.png)|
|1|Bottom|![User handle for node in blazor diagram](images/userhandle9.png)|

### Size

Diagram allows you set size for user handles by using the `Size` property. The default value of the `Size` property is 25.

### Style

You can change the style of the user handles with the specific properties of PathColor, BorderColor, BackgroundColor and BorderWidth. The following code explains how to customize the appearance of the user handles.

* The user handle's `PathColor` property used to change the color of the given `PathData` of the user handle.

* The user handle `BorderColor`, `BackgroundColor` properties are used to define the background color and border color of the user handle and the `BorderWidth` property is used to define the border width of the user handles.

* The `Visible` property of the user handle enables or disables the visibility of user handle.

The following code explains how to customize the appearance of the user handle.

```cshtml
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px"
                    Nodes="@nodes"
                    SelectedItems="@SelectedModel">
    <SnapSettings>
        <HorizontalGridLines LineColor="White" LineDashArray="2,2"/>
        <VerticalGridLines LineColor="White" LineDashArray="2,2"/>
    </SnapSettings>
</SfDiagramComponent>

@code
{
    // Defines diagram's nodes collection
    DiagramObjectCollection<Node> nodes = new DiagramObjectCollection<Node>();
    // Defines diagram's SelectedItems
    Selector SelectedModel = new Selector();
    DiagramObjectCollection<UserHandle> UserHandles = new DiagramObjectCollection<UserHandle>();

    protected override void OnInitialized()
    {
        //Creating the userhandle for cloning the objects
        UserHandle cloneHandle = new UserHandle()
        {
            //Name of the user handle
            Name = "clone",
            //Set pathdata for userhandle
            PathData = "M60.3,18H27.5c-3,0-5.5,2.4-5.5,5.5v38.2h5.5V23.5h32.7V18z M68.5,28.9h-30c-3,0-5.5,2.4-5.5,5.5v38.2c0,3,2.4,5.5,5.5,5.5h30c3,0,5.5-2.4,5.5-5.5V34.4C73.9,31.4,71.5,28.9,68.5,28.9z M68.5,72.5h-30V34.4h30V72.5z",
            //Set visibility for the user handle
            Visible = true,
            //Set the position for the user handle
            Offset = 1,
            //Set side based on the given offset
            Side = Side.Bottom,
            //set margin for the user handle
            Margin = new Margin() { Top = 0, Bottom = 0, Left = 0, Right = 0 },
            //Set size of the user handle
            Size = 50,
            //Set pathcolor for given pathdata
            PathColor = "yellow",
            //Set Border color of the user handle
            BorderColor = "red",
            //Set Background Color of the user handle
            BackgroundColor = "green",
            //Set Border Width Color of the user handle
            BorderWidth = 3,
        };
        //Add user handle to the collection...
        UserHandles = new DiagramObjectCollection<UserHandle>()
        {
            cloneHandle
        };
        SelectedModel = new Selector()
        {
            //Enable userhandle for selected items...
            Constraints = SelectorConstraints.UserHandle,
            UserHandles = this.UserHandles
        };
        nodes = new DiagramObjectCollection<Node>();
        Node diagramNode = new Node()
        {
            ID = "node1",
            OffsetX = 100,
            OffsetY = 100,
            Width = 100,
            Height = 100,
            Style = new ShapeStyle() { Fill = "#6495ED", StrokeColor = "none" },
            Annotations = new DiagramObjectCollection<ShapeAnnotation>() { new ShapeAnnotation { Content = "Node" } }
        };
        nodes.Add(diagramNode);
    }
}
```

![Customized appearance of Userhandle](images/userhandle10.png)

## Fixed user handles

 The fixed user handles are used to add some frequently used commands around the node and connector even without selecting it.

## Initialization an fixed user handles

To create the fixed user handles, define and add them to the collection of nodes and connectors property. The following code example used to create an fixed user handles for the  nodes and connectors.

```cshtml
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Nodes="@nodes" />

@code
{
    // Defines diagram's nodes collection
    DiagramObjectCollection<Node> nodes = new DiagramObjectCollection<Node>();

    protected override void OnInitialized()
    {
        nodes = new DiagramObjectCollection<Node>();
        Node node1 = new Node()
        {
            OffsetX = 250,
            OffsetY = 250,
            Width = 100,
            Height = 100,
            Style = new ShapeStyle() { Fill = "#6495ED", StrokeColor = "white" },
            // A fixed user handle is created and stored in fixed user handle collection of Node.
            FixedUserHandles = new DiagramObjectCollection<NodeFixedUserHandle>()
            {
                new NodeFixedUserHandle() 
                { 
                    ID = "user1",
                    Height = 20, 
                    Width = 20, 
                    Visibility = true,
                    Padding = new Margin(){Bottom=1,Left=1,Right=1,Top=1 }, 
                    Margin = new Margin(){ Right = 20},Offset = new Point() { X =0 , Y = 0 }, 
                    PathData = "M60.3,18H27.5c-3,0-5.5,2.4-5.5,5.5v38.2h5.5V23.5h32.7V18z M68.5,28.9h-30c-3,0-5.5,2.4-5.5,5.5v38.2c0,3,2.4,5.5,5.5,5.5h30c3,0,5.5-2.4,5.5-5.5V34.4C73.9,31.4,71.5,28.9,68.5,28.9z M68.5,72.5h-30V34.4h30V72.5z" 
                },
            }
        };
        nodes.Add(node1);
    }
}
```

## Customization the fixed user handle

* The id property of fixed user handle is used to define the unique identification of the fixed user handle and it is further used to add custom events to the fixed user handle.

* The fixed user handle can be positioned relative to the node and connector boundaries. It has offset, padding and cornerRadius settings. It is used to position and customize the fixed user handle.

* The `Padding` is used to leave the space that is inside the fixed user handle between the icon and border.

* The corner radius allows to create fixed user handles with rounded corners. The radius of the rounded corner is set with the `cornerRadius` property.

> The PathData needs to be provided to render fixed user handle.

### Size

 Diagram allows you set size for the fixed user handles by using the `width` and `height` property. The default value of the width and height property is 10.

### Style

* You can change the style of the fixed user handles with the specific properties of borderColor, borderWidth, and background color using the handleStrokeColor, handleStrokeWidth, and fill properties, and the icon borderColor, and borderWidth using the iconStrokeColor and iconStrokeWidth.

* The fixed user handle's `iconStrokeColor` and `iconStrokeWidth` property used to change the stroke color and stroke width of the given `pathData`.

* The fixed user handle `handleStrokeColor` and `fill` properties are used to define the background color and border color of the user handle and the `handleStrokeWidth` property is used to define the border width of the fixed user handle.

* The `visible` property of the fixed user handle enables or disables the visibility of fixed user handle.

The following code explains how to customize the appearance of the fixed user handles.

```cshtml
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Connectors="@connectors">
    <SnapSettings>
        <HorizontalGridLines LineColor="White" LineDashArray="2,2"/>
        <VerticalGridLines LineColor="White" LineDashArray="2,2"/>
    </SnapSettings>
</SfDiagramComponent>

@code
{
    DiagramObjectCollection<Connector> connectors = new DiagramObjectCollection<Connector>();

    protected override void OnInitialized()
    {
        connectors = new DiagramObjectCollection<Connector>();
        Connector connector = new Connector()
        {
            SourcePoint = new Point() { X = 100, Y = 100 },
            TargetPoint = new Point() { X = 200, Y = 200 },
            Type = Segments.Orthogonal,
            Style = new TextShapeStyle() { StrokeColor = "#6495ED" },
            // A fixed user handle is created and stored in fixed user handle collection of Connector.
            FixedUserHandles = new DiagramObjectCollection<ConnectorFixedUserHandle>()
            {
                new ConnectorFixedUserHandle() 
                { 
                    ID = "user1",
                    Height = 25, 
                    Width = 25,
                    Offset = 0.5,
                    Alignment = FixedUserHandleAlignment.After,
                    Displacement = new Point{Y= 10},
                    Visibility = true,Padding = new Margin(){Bottom=1,Left=1,Right=1,Top=1 },
                    PathData = "M60.3,18H27.5c-3,0-5.5,2.4-5.5,5.5v38.2h5.5V23.5h32.7V18z M68.5,28.9h-30c-3,0-5.5,2.4-5.5,5.5v38.2c0,3,2.4,5.5,5.5,5.5h30c3,0,5.5-2.4,5.5-5.5V34.4C73.9,31.4,71.5,28.9,68.5,28.9z M68.5,72.5h-30V34.4h30V72.5z"
                }
            },
        };
        connectors.Add(connector);
    }
}
```

> The fixed user handle id need to be unique.

## Customizing the node fixed user handle

The node fixed user handle can be aligned relative to the node boundaries. It has `margin` and `offset` settings. It is quite useful to position the node fixed user handle and used together and gives you more control over the node fixed user handle positioning.

### Margin for the node fixed user handle

Margin is an absolute value used to add some blank space in any one of its four sides. The fixed user handle can be displaced with the `margin` property.

### Offset for the node fixed user handle

The `offset` property of fixed user handle is used to align the user handle based on the `x` and `y` points. (0,0) represents the top or left corner and (1,1) represents the bottom or right corner.

The following table shows all the possible alignments visually shows the fixed user handle positions.

| Offset | Margin | Output |
| -------- | -------- | -------- |
| (0,0) | Right = 20 |![fixed user handle for node in blazor diagram](images/topleft.png)|
| (0.5,0) | Bottom = 20 |![fixed user handle for node in blazor diagram](images/topcenter.png)|
| (1,0) | Left = 20 |![fixed user handle for node in blazor diagram](images/topright.png)|
| (0,0.5) | Right = 20 |![fixed user handle for node in blazor diagram](images/leftcenter.png)|
| (1,0.5) | Left = 20 |![fixed user handle for node in blazor diagram](images/rightcenter.png)|
| (0,1) | Right = 20 |![fixed user handle for node in blazor diagram](images/bottomleft.png)|
| (0.5,1) | Top = 20 |![fixed user handle for node in blazor diagram](images/bottomcenter.png)|
| (1,1) | Left = 20 |![fixed user handle for node in blazor diagram](images/bottomright.png)|

The following code explains how to customize the node fixed user handle.

```cshtml
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px"
                    Nodes="@nodes">
    <SnapSettings>
        <HorizontalGridLines LineColor="White" LineDashArray="2,2"/>
        <VerticalGridLines LineColor="White" LineDashArray="2,2"/>
    </SnapSettings>
</SfDiagramComponent>

@code
{
    // Defines diagram's nodes collection
    DiagramObjectCollection<Node> nodes = new DiagramObjectCollection<Node>();

    protected override void OnInitialized()
    {
        //Creating the userhandle for cloning the objects
        nodes = new DiagramObjectCollection<Node>();
        Node diagramNode = new Node()
        {
            OffsetX = 250,
            OffsetY = 250,
            Width = 100,
            Height = 100,
            Style = new ShapeStyle() { Fill = "#6495ED", StrokeColor = "white" },
            // A fixed user handle is created and stored in fixed user handle collection of Node.
            FixedUserHandles = new DiagramObjectCollection<NodeFixedUserHandle>()
            {
                new NodeFixedUserHandle() 
                { 
                    ID = "user1",
                    Height = 20, 
                    Width = 20, 
                    Visibility = true,
                    Padding = new Margin(){Bottom=1,Left=1,Right=1,Top=1 },
                    Margin = new Margin(){ Left = 20},
                    Offset = new Point() { Y = 0},
                    PathData = "M60.3,18H27.5c-3,0-5.5,2.4-5.5,5.5v38.2h5.5V23.5h32.7V18z M68.5,28.9h-30c-3,0-5.5,2.4-5.5,5.5v38.2c0,3,2.4,5.5,5.5,5.5h30c3,0,5.5-2.4,5.5-5.5V34.4C73.9,31.4,71.5,28.9,68.5,28.9z M68.5,72.5h-30V34.4h30V72.5z"
                },
            }
        };
        nodes.Add(diagramNode);
    }
}
```

## Customizing the connector fixed user handle

* The connector fixed user handle can be aligned relative to the connector boundaries. It has alignment, displacement and offset settings. It is useful to position the connector fixed user handle and used together and gives you more control over the connector fixed user handle positioning.

* The `offset` and `alignment` properties of fixed user handle allows you to align the connector fixed user handles to the segments.

### Offset for the connector fixed user handle

The `offset` property of connector fixed user handle is used to align the user handle based on fractions. 0 represents the connector source point, 1 represents the connector target point, and 0.5 represents the center point of the connector segment.

### Alignment

The connector’s fixed user handle can be aligned over its segment path using the `alignment` property of fixed user handle.

The following table shows all the possible alignments visually shows the fixed user handle positions.

| Offset | Alignment | Output |
| -------- | -------- | -------- |
| 0 | Before |![fixed user handle for node in blazor diagram](images/before.png)|
| 0.5 | Center |![fixed user handle for node in blazor diagram](images/center.png)|
| 1 | After |![fixed user handle for node in blazor diagram](images/after.png)|

### Displacement

* The `displacement` property allows you to specify the space to be left from the connector segment based on the x and y value provided.

The following table shows all the possible alignments visually shows the fixed user handle positions.

| Displacement | Alignment | Output |
| -------- | -------- | -------- |
| y=10 | Before |![fixed user handle for node in blazor diagram](images/ybefore.png)|
| y=10 | After |![fixed user handle for node in blazor diagram](images/yafter.png)|

> Displacement will not be done if the alignment is set to be center.

The following code explains how to customize the connector fixed user handle.

```cshtml
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Connectors="@connectors">
    <SnapSettings>
        <HorizontalGridLines LineColor="White" LineDashArray="2,2"/>
        <VerticalGridLines LineColor="White" LineDashArray="2,2"/>
    </SnapSettings>
</SfDiagramComponent>

@code
{
    DiagramObjectCollection<Connector> connectors = new DiagramObjectCollection<Connector>();

    protected override void OnInitialized()
    {
        connectors = new DiagramObjectCollection<Connector>();
        Connector connector = new Connector()
        {
            SourcePoint = new Point() { X = 100, Y = 100 },
            TargetPoint = new Point() { X = 200, Y = 200 },
            Type = Segments.Orthogonal,
            Style = new TextShapeStyle() { StrokeColor = "#6495ED" },
            // A fixed user handle is created and stored in fixed user handle collection of Connector.
            FixedUserHandles = new DiagramObjectCollection<ConnectorFixedUserHandle>()
            {
                new ConnectorFixedUserHandle()
                {
                    ID = "user1",
                    Height = 25,
                    Width = 25,
                    Offset = 0.5,
                    Alignment = FixedUserHandleAlignment.After,
                    Displacement = new Point { Y = 10 },
                    Visibility = true, Padding = new Margin() { Bottom = 1, Left = 1, Right = 1, Top = 1 },
                    PathData = "M60.3,18H27.5c-3,0-5.5,2.4-5.5,5.5v38.2h5.5V23.5h32.7V18z M68.5,28.9h-30c-3,0-5.5,2.4-5.5,5.5v38.2c0,3,2.4,5.5,5.5,5.5h30c3,0,5.5-2.4,5.5-5.5V34.4C73.9,31.4,71.5,28.9,68.5,28.9z M68.5,72.5h-30V34.4h30V72.5z"
                }
            }
        };
        connectors.Add(connector);
    }
}
```

## FixedUserHandle Event

The Diagram control provides following event for the fixed user handle.

| Event Name | Event Type | Description |
| -------- | -------- | -------- |
| FixedUserHandleClick | FixedUserHandleClickEventArgs | Triggered when the mouse pointer is over the user handle and mouse button is up. |

```cshtml
@using Syncfusion.Blazor.Diagram
@using System.Collections.ObjectModel

<SfDiagramComponent Height="600px"
                    FixedUserHandleClick="Changed" Nodes="@nodes" @ref="diagram">
</SfDiagramComponent>

@code
{
    SfDiagramComponent diagram;

    public async void Changed(FixedUserHandleClickEventArgs args)
    {
        if ((args.Element as Node).ID == "node1" && args.FixedUserHandle.ID == "user1")
        {
            diagram.Copy();
            diagram.Paste();
        }
    }

    DiagramObjectCollection<Node> nodes = new DiagramObjectCollection<Node>();

    protected override void OnInitialized()
    {
        nodes = new DiagramObjectCollection<Node>();
        Node node1 = new Node()
        {
            OffsetX = 250,
            OffsetY = 250,
            ID = "node1",
            Width = 100,
            Height = 100,
            Style = new ShapeStyle() { Fill = "#6BA5D7", StrokeColor = "white" },
            // A fixed user handle is created and stored in fixed user handle collection of Node.
            FixedUserHandles = new DiagramObjectCollection<NodeFixedUserHandle>()
            {
                new NodeFixedUserHandle()
                {
                    ID = "user1",
                    Height = 20, 
                    Width = 20, 
                    Visibility = true,
                    Padding = new Margin(){Bottom=1,Left=1,Right=1,Top=1 }, 
                    Margin = new Margin(){ Right = 20},
                    Offset = new Point() { X =0 , Y = 0 }, 
                    PathData = "M60.3,18H27.5c-3,0-5.5,2.4-5.5,5.5v38.2h5.5V23.5h32.7V18z M68.5,28.9h-30c-3,0-5.5,2.4-5.5,5.5v38.2c0,3,2.4,5.5,5.5,5.5h30c3,0,5.5-2.4,5.5-5.5V34.4C73.9,31.4,71.5,28.9,68.5,28.9z M68.5,72.5h-30V34.4h30V72.5z" 
                },
            }
        };
        nodes.Add(node1);
    }
}
```