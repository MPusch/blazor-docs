# Appearance

* The appearance of a node can be customized by changing its `Fill`, `StrokeDashArray`, `StrokeColor`, `StrokeWidth`, and `Shadow` properties.

* The `Visible` property of the node enables or disables the visibility of the node.

The following code shows how to customize the appearance of the shape.

```csharp
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Nodes="@NodeCollection">
</SfDiagramComponent>

@code{
    DiagramObjectCollection<Node> NodeCollection = new DiagramObjectCollection<Node>();
    protected override void OnInitialized()
    {
        // A node is created and stored in nodes array.
        Node node = new Node()
        {
            // Position of the node
            OffsetX = 250,
            OffsetY = 250,
            // Size of the node
            Width = 100,
            Height = 100,
            // Add node
            Style = new ShapeStyle() { Fill = "Green", StrokeDashArray = "5,5", StrokeColor = "red", StrokeWidth = 2 },
        };
        NodeCollection.Add(node);
    }
}
```

![Node appearance](../images/node_appearance.png)

>**Note:**
>* `ID` for each node should be unique and so it is further used to find the node at runtime and do any customization.

## NodeDefaults

Default values for all the Nodes can be set using the NodeDefaults properties. For example, if all nodes have the same type or having the same property then such properties can be moved into NodeDefaults.

The following code shows how to customize the appearance of the shape.

```csharp
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Nodes="@NodeCollection" NodeDefaults="@NodeDefaults"/>

@code{
    DiagramObjectCollection<Node> NodeCollection = new DiagramObjectCollection<Node>();
    protected override void OnInitialized()
    {
        // A node is created and stored in nodes array.
        Node node1 = new Node()
        {
            // Position of the node
            OffsetX = 250,
            OffsetY = 250,
            // Shape of the Node
            Shape=new BasicShape() {Type= Shapes.Basic, Shape = BasicShapes.Rectangle}
        };
        Node node2 = new Node()
        {
            // Position of the node
            OffsetX = 100,
            OffsetY = 100,
            // Shape of the Node
            Shape = new BasicShape() { Type = Shapes.Basic, Shape = BasicShapes.Ellipse }
        };
        NodeCollection.Add(node1);
        NodeCollection.Add(node2);
    }

    private void NodeDefaults(IDiagramObject obj)
    {
        Node node = obj as Node;
        node.Style = new ShapeStyle() { Fill = "#6495ED"};
        // Size of the node
        node.Width = 100;
        node.Height = 100;
    }
}
```

## NodeTemplate

We can define multiple node templates in NodeTemplate by differentiating the nodes by the ID property .The following code explains how to define multiple templates.

```csharp
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent @ref="diagram" Width="1200px" Height="1000px" Nodes="@nodes">
    <SnapSettings Constraints="SnapConstraints.None"></SnapSettings>
    <DiagramTemplates>
        <NodeTemplate>
            @{ var id = (context as Node).ID;
                if (id == "html1")
                {
                    <div style="height: 100%; width: 100%; background:cornflowerblue">
                        <input type="button" value="Button" />
                    </div>
                }
                else if (id == "html2")
                {
                    <style>
                        th {
                            border: 5px solid #c1dad7
                        }

                        td {
                            border: 5px solid #c1dad7
                        }

                        .c1 {
                            background: #4b8c74
                        }

                        .c2 {
                            background: #74c476
                        }

                        .c3 {
                            background: #a4e56d
                        }

                        .c4 {
                            background: #cffc83
                        }
                    </style>
                    <div id="node0_content_html_element" class="foreign-object" style="height: 164px; width: 137px; left: 0px; top: 0px; position: absolute; transform: scale(1, 1) rotate(0deg); pointer-events: all; visibility: visible; opacity: 1;"><div style="height: 100%; width: 100%;"><table style="width:100%;"><tbody><tr><th class="c1">ID</th><th class="c2">Offset</th></tr><tr><td class="c1">node0</td><td class="c2">100</td></tr></tbody></table></div></div>
                }
            }
        </NodeTemplate>
    </DiagramTemplates>
</SfDiagramComponent>

@code{
    SfDiagramComponent diagram;
    DiagramObjectCollection<Node> nodes = new DiagramObjectCollection<Node>();
    protected override void OnInitialized()
    {
        nodes = new DiagramObjectCollection<Node>(){
        new Node()
        {
            Width =100,
            Height = 100,
            OffsetX = 100,
            OffsetY = 100,
            ID = "html1",
            Shape = new Shape() { Type = Shapes.HTML },
            Visible = true,
        },
         new Node()
         {  
            Width = 137,
            Height = 64,
            OffsetX = 300,
            OffsetY = 100,
            ID = "html2",
            Shape = new Shape() { Type = Shapes.HTML},
          },
    };
    }
}
```

![Node Template](../images/Multipletemplate.png)

## SetNodeTemplate

The `SetNodeTemplate` method of diagram allows you to define the style for the Node. The following code demonstrates how to use SetNodeTemplate method.

```csharp
@using Syncfusion.Blazor.Diagram

@* Initialize Diagram *@
<SfDiagramComponent Height="600px" Nodes="@NodeCollection" SetNodeTemplate="@SetNodeTemplate">
</SfDiagramComponent>

@code{
    //Initialize node collection with node
    DiagramObjectCollection<Node> NodeCollection = new DiagramObjectCollection<Node>()
{
        //Creates a text node
         new Node()
         {
             ID="node1",
             // Size of the node
             Height=100,
             Width=100,
             // Position of the node
             OffsetX=100,
             OffsetY=100,
         }
     };
    private ICommonElement SetNodeTemplate(IDiagramObject node)
    {
       (node as Node).Style = new ShapeStyle() { StrokeColor = "#6F409F", StrokeWidth = 2 };
       (node as Node).Shape = new BasicShape() { Type = Shapes.Basic, Shape = BasicShapes.Rectangle, CornerRadius = 10 };
    }
}
```

![SetNodeTemplate](../images/SetTemplate.png)

## Shadow

Diagram provides support to add `Shadow` effect to a node that is disabled, by default. It can be enabled with the
constraints property of the node. The following code shows how to draw shadow.

```csharp
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Nodes="@NodeCollection">
</SfDiagramComponent>

@code{

    DiagramObjectCollection<Node> NodeCollection = new DiagramObjectCollection<Node>() { };
    protected override void OnInitialized()
    {
        // A node is created and stored in nodes array.
        Node node = new Node()
        {
            // Position of the node
            OffsetX = 250,
            OffsetY = 250,
            // Size of the node
            Width = 100,
            Height = 100,
            Style = new ShapeStyle() { Fill = "#6BA5D7", StrokeColor = "white" },
            Constraints = NodeConstraints.Default | NodeConstraints.Shadow
        };
        NodeCollection.Add(node);
    }
}
```

![Node shadow](../images/node_shadow.png)

### Customizing shadow

The `Angle`, `Distance`, and `Opacity` of the shadow can be customized with the shadow property of the node. The following code
example illustrates how to customize shadow.

```csharp
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Nodes="@NodeCollection">
</SfDiagramComponent>

@code{

    DiagramObjectCollection<Node> NodeCollection = new DiagramObjectCollection<Node>() { };
    protected override void OnInitialized()
    {
        // A node is created and stored in nodes array.
        Node node = new Node()
        {
            // Position of the node
            OffsetX = 250,
            OffsetY = 250,
            // Size of the node
            Width = 100,
            Height = 100,
            Style = new ShapeStyle() { Fill = "#6BA5D7", StrokeColor = "white" },
            Constraints = NodeConstraints.Default | NodeConstraints.Shadow,
            // Custom Shadow of the node
            Shadow = new Shadow()
            {
                Angle = 50,
                Opacity = 0.8,
                Distance = 9
            }
        };
        NodeCollection.Add(node);
    }
}
```

![Shadow](../images/customshadow.png)

## Gradient

The `Gradient` property of the node allows you to define and apply the gradient effect to the node.

The gradient stop property defines the color and a position, where the previous color transition ends and a new color transition starts.

The gradient stop’s opacity property defines the transparency level of the region.

There are two types of gradients as follows:

* Linear Gradient

* Radial Gradient

### Linear gradient

* `LinearGradient` defines a smooth transition between a set of colors (so-called stops) in a line.

* A linear gradient’s X1, Y1, X2, Y2 properties are used to define the position (relative to the node) of the rectangular region that needs to be painted.

```csharp
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Nodes="@NodeCollection">
</SfDiagramComponent>

@code{
    DiagramObjectCollection<Node> NodeCollection = new DiagramObjectCollection<Node>() { };
    protected override void OnInitialized()
    {
        // A node is created and stored in nodes array.
        Node node = new Node()
        {
            // Position of the node
            OffsetX = 250,
            OffsetY = 250,
            // Size of the node
            Width = 100,
            Height = 100,
            Style = new ShapeStyle()
            {
                Gradient = new LinearGradient()
                {
                    //Start point of linear gradient
                    X1 = 0,
                    Y1 = 0,
                    ////End point of linear gradient
                    X2 = 50,
                    Y2 = 50,
                    //Sets an array of stop objects
                    Stops = new DiagramObjectCollection<GradientStop>()
                {
                        new GradientStop(){ Color = "white", Offset = 0},
                        new GradientStop(){ Color = "#6BA5D7", Offset = 100}
                    },
                    Type = GradientType.Linear
                }
            },
        };
        NodeCollection.Add(node);
    }
}
```

![Node LinearGradient](../images/node_lineargradient.png)

### Radial gradient

* `RadialGradient` defines a smooth transition between stops on a circle.

* A radial gradient properties are used to define the position (relative to the node) of the outermost or the innermost circle of the radial gradient.

```csharp
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Nodes="@NodeCollection">
</SfDiagramComponent>

@code{
    DiagramObjectCollection<Node> NodeCollection = new DiagramObjectCollection<Node>();
    protected override void OnInitialized()
    {
        Node node = new Node()
        {
            // Position of the node
            OffsetX = 250,
            OffsetY = 250,
            // Size of the node
            Width = 100,
            Height = 100,
            Style = new ShapeStyle()
            {
                Gradient = new RadialGradient()
                {
                    //Center point of inner circle
                    Fx = 20,
                    Fy = 20,
                    //Center point of outer circle
                    Cx = 50,
                    Cy = 50,
                    //Radius of a radial gradient
                    R = 50,
                    //Sets an array of stop objects
                    Stops = new DiagramObjectCollection<GradientStop>()
                    {
                        new GradientStop(){ Color = "white", Offset = 0},
                        new GradientStop(){ Color = "#6BA5D7", Offset = 100}
                    },
                    Type = GradientType.Radial
                }
            },
        };
        // Add node
        NodeCollection.Add(node);
    }
}
```

![Node RadialGradient](../images/node_radialgradient.png)

## Custom properties

The `AddInfo` property of the node allows you to maintain additional information to the node.

The following code shows how to set the `AddInfo` value.

```csharp
@using Syncfusion.Blazor.Diagram

<SfDiagramComponent Height="600px" Nodes="@NodeCollection">
</SfDiagramComponent>

@code{

    DiagramObjectCollection<Node> NodeCollection = new DiagramObjectCollection<Node>();
    protected override void OnInitialized()
    {
        Dictionary<string, object> NodeInfo = new Dictionary<string, object>();
        NodeInfo.Add("nodeInfo", "Central Node");
        // A node is created and stored in nodes collection.

        Node node = new Node()
        {
            // Position of the node
            OffsetX = 250,
            OffsetY = 250,
            // Size of the node
            Width = 100,
            Height = 100,
            Style = new ShapeStyle() { Fill = "#6BA5D7", StrokeColor = "white" },
            AddInfo = NodeInfo
        };
        // Add node
        NodeCollection.Add(node);
    }
}
```

**Note:** We can set any type of value for the AddInfo property.

## See also

* [`How to get events when they interact the node`](./events)
