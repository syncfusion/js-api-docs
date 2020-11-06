---
layout: post
title: Shape colors in Syncfusion Flutter Maps | Syncfusion
description: This section explains about shapes and how to apply colors to the shapes based on specific values in the Flutter maps.
platform: Flutter
control: SfMaps
documentation: ug
---

# Shapes in the Flutter Maps

This section explains about shapes and how to apply colors to the shapes based on specific values in the Flutter maps.

## Loading progress indicator

You can notify the user that the map is being loaded using the [`MapShapeLayer.loadingBuilder`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/loadingBuilder.html). It returns the widget which will be visible till the maps is loaded.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: EdgeInsets.all(15),
        child: SfMaps(
          layers: <MapLayer>[
            MapShapeLayer(
              delegate: MapShapeLayerDelegate(
                shapeFile: 'assets/world_map.json',
                shapeDataField: 'continent',
              ),
              loadingBuilder: (BuildContext context) {
                return Container(
                  height: 25,
                  width: 25,
                  child: const CircularProgressIndicator(
                    strokeWidth: 3,
                  ),
                );
              },
            ),
          ],
        ),
      ),
   );
}

{% endhighlight %}
{% endtabs %}

![Loading builder](images/shape-colors/loading-builder.gif)

## Shape color

You can apply color, stroke color and stroke width to the shapes using the [`MapShapeLayer.color`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/color.html), [`MapShapeLayer.strokeColor`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/strokeColor.html) and [`MapShapeLayer.strokeWidth`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/strokeWidth.html) properties respectively.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
      body: Padding(
        padding: EdgeInsets.all(15),
        child: SfMaps(
          layers: <MapLayer>[
            MapShapeLayer(
              color: Colors.blue[100],
              strokeColor: Colors.blue,
              strokeWidth: 2,
              delegate: MapShapeLayerDelegate(
                shapeFile: 'assets/world_map.json',
                shapeDataField: 'continent',
              ),
            ),
          ],
        ),
      ),
   );
}

{% endhighlight %}
{% endtabs %}

<b>Using SfMapsTheme</b>

You can also customize the below appearance of the shape using [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

* **Color** - Change the color of the shapes using the [`SfMapsThemeData.layerColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/layerColor.html) property.
* **Stroke color** - Change the stroke color of the shapes using the [`SfMapsThemeData.layerStrokeColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/layerStrokeColor.html) property.
* **Stroke width** - Change the stroke width of the shapes using the [`SfMapsThemeData.layerStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/layerStrokeWidth.html) property.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
      body: Padding(
        padding: EdgeInsets.all(15),
        child: SfMapsTheme(
          data: SfMapsThemeData(
            layerColor: Colors.blue[100],
            layerStrokeColor: Colors.blue,
            layerStrokeWidth: 2
          ),
          child: SfMaps(
            layers: <MapLayer>[
              MapShapeLayer(
                delegate: MapShapeLayerDelegate(
                  shapeFile: 'assets/world_map.json',
                  shapeDataField: 'continent',
                ),
              ),
            ],
          ),
        )
      ),
   );
}

{% endhighlight %}
{% endtabs %}

![Shapes color](images/shape-colors/shapes-stroke-color.png)

## Hover color

You can apply hover color, stroke color and stroke width to the shapes in the web platform using the [`SfMapsThemeData.shapeHoverColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/shapeHoverColor.html), [`SfMapsThemeData.shapeHoverStrokeColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/shapeHoverStrokeColor.html) and [`SfMapsThemeData.shapeHoverStrokeWidth`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsThemeData/shapeHoverStrokeWidth.html) properties respectively.

N> You must import the `theme.dart` library from the [`Core`](https://pub.dev/packages/syncfusion_flutter_core) package to use [`SfMapsTheme`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfMapsTheme-class.html).

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
      body: Padding(
        padding: EdgeInsets.all(15),
        child: SfMapsTheme(
          data: SfMapsThemeData(
            shapeHoverColor: Colors.red[800],
            shapeHoverStrokeColor: Colors.black,
            shapeHoverStrokeWidth: 2,
          ),
          child: SfMaps(
            layers: <MapLayer>[
              MapShapeLayer(
                delegate: MapShapeLayerDelegate(
                  shapeFile: 'assets/world_map.json',
                  shapeDataField: 'continent',
                ),
              ),
            ],
          ),
        )
      ),
   );
}

{% endhighlight %}
{% endtabs %}

## Palette

You can color the shape based on the list of colors provided in the [`MapShapeLayer.palette`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/palette.html) property in a sequential order.

If the number of shapes exceeds the length of this collections, once the last color is used for a shape, color in the 0th index will be used for the next shape and so on.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
      body: Padding(
        padding: EdgeInsets.all(15),
        child: SfMaps(
          layers: <MapLayer>[
            MapShapeLayer(
              delegate: MapShapeLayerDelegate(
                shapeFile: 'assets/world_map.json',
                shapeDataField: 'continent',
              ),
              palette: <Color>[
                Colors.blue[200],
                Colors.orange[200],
                Colors.red[200],
                Colors.green[200],
                Colors.purple[200],
                Colors.lime[200]
              ],
            ),
          ],
        ),
      ),
   );
}

{% endhighlight %}
{% endtabs %}

![Shapes palette](images/shape-colors/shapes-palette.png)

## Applying colors based on the data

If you return a color from the [`shapeColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeColorValueMapper.html), then the color will be applied to the respective shape straightaway.

If you return a value of different type other than the color from the [`shapeColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeColorValueMapper.html), then you must set the [`MapShapeLayer.shapeColorMappers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeColorMappers.html) property which is a collection of [`MapColorMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper-class.html) to apply colors for the respective shapes.

N> You can show legend using the [`MapShapeLayer.showLegend`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayer/showLegend.html) property. The icons color of the legend is applied based on the colors returned in the [`MapShapeLayerDelegate.shapeColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeColorValueMapper.html) property and the text will be taken from the [`primaryValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/primaryValueMapper.html). It is possible to customize the legend icons color and text using the [`MapShapeLayerDelegate.shapeColorMappers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeColorMappers.html) property.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    data = const <Model>[
      Model('Asia', Color.fromRGBO(60, 120, 255, 0.8)),
      Model('Africa', Color.fromRGBO(51, 102, 255, 0.8)),
      Model('Europe', Color.fromRGBO(0, 57, 230, 0.8)),
      Model('South America', Color.fromRGBO(0, 51, 204, 0.8)),
      Model('Australia', Color.fromRGBO(0, 45, 179, 0.8)),
      Model('North America', Color.fromRGBO(0, 38, 153, 0.8))
    ];
    super.initState();
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
          child: Container(
        height: 350,
        child: Padding(
          padding: EdgeInsets.only(left: 15, right: 15),
          child: SfMaps(
            layers: <MapLayer>[
              MapShapeLayer(
                delegate: MapShapeLayerDelegate(
                  shapeFile: 'assets/world_map.json',
                  shapeDataField: 'continent',
                  dataCount: data.length,
                  primaryValueMapper: (int index) => data[index].country,
                  shapeColorValueMapper: (int index) => data[index].color,
                ),
              ),
            ],
          ),
        ),
      )),
   );
}

class Model {
  const Model(this.country, this.color);

  final String country;
  final Color color;
}

{% endhighlight %}
{% endtabs %}

![Shape color](images/shape-colors/shape_color_default.png)

## Equal color mapping

You can apply color to the shape by comparing a value that returns from the [`shapeColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeColorValueMapper.html) with the [`MapColorMapper.value`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/value.html). For the matched values, the [`MapColorMapper.color`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/color.html) will be applied to the respective shapes.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    super.initState();
    data = <Model>[
      Model('India', "Low"),
      Model('United States of America', "High"),
      Model('Pakistan', "Low"),
    ];
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: EdgeInsets.only(left: 15, right: 15),
        child: SfMaps(
          layers: <MapShapeLayer>[
            MapShapeLayer(
              delegate: MapShapeLayerDelegate(
                  shapeFile: "assets/world_map.json",
                  shapeDataField: "name",
                  dataCount: data.length,
                  primaryValueMapper: (int index) {
                    return data[index].country;
                  },
                  shapeColorValueMapper: (int index) {
                    return data[index].storage;
                  },
                  shapeColorMappers: [
                    MapColorMapper(value: "Low", color: Colors.red),
                    MapColorMapper(value: "High", color: Colors.green)
                  ]),
            )
          ],
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.storage);

  final String country;
  final String storage;
}

{% endhighlight %}
{% endtabs %}

![Equal color mapping](images/shape-colors/equal_color_mapping.png)

## Range color mapping

You can apply color to the shape based on whether the value returned from [`shapeColorValueMapper`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/shapeColorValueMapper.html) falls within the [`MapColorMapper.from`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/from.html) and [`MapColorMapper.to`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/to.html). Then, the [`MapColorMapper.color`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/color.html) will be applied to the respective shapes.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    super.initState();

    data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
    ];
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: EdgeInsets.only(left: 15, right: 15),
        child: SfMaps(
          layers: [
            MapShapeLayer(
              delegate: MapShapeLayerDelegate(
                  shapeFile: "assets/world_map.json",
                  shapeDataField: "name",
                  dataCount: data.length,
                  primaryValueMapper: (int index) => data[index].country,
                  shapeColorValueMapper: (int index) => data[index].count,
                  shapeColorMappers: [
                    MapColorMapper(from: 0, to: 100, color: Colors.red),
                    MapColorMapper(from: 101, to: 300, color: Colors.green)
                  ]
               ),
            )
          ],
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.count);

  final String country;
  final double count;
}

{% endhighlight %}
{% endtabs %}

![Range color mapping](images/shape-colors/range_color_mapping.png)

## Opacity

You can apply the maximum and minimum opacity to the shape or [`bubbles`](https://help.syncfusion.com/flutter/maps/bubble) while using [`MapColorMapper.from`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/from.html) and [`MapColorMapper.to`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/to.html) properties.

The shapes or bubbles with lowest value which is [`from`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/from.html) will be applied a [`minOpacity`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/minOpacity.html) and the shapes or bubbles with highest value which is [`to`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/to.html) will be applied a [`maxOpacity`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapColorMapper/maxOpacity.html). The shapes or bubbles with values in-between the range will get a opacity based on their respective value.

{% tabs %}
{% highlight Dart %}

List<Model> data;

@override
void initState() {
    super.initState();

    data = <Model>[
      Model('India', 280),
      Model('United States of America', 190),
      Model('Kazakhstan', 37),
    ];
}

@override
Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: EdgeInsets.only(left: 15, right: 15),
        child: SfMaps(
          layers: [
            MapShapeLayer(
              delegate: MapShapeLayerDelegate(
                  shapeFile: "assets/world_map.json",
                  shapeDataField: "name",
                  dataCount: data.length,
                  primaryValueMapper: (int index) => data[index].country,
                  shapeColorValueMapper: (int index) => data[index].count,
                  shapeColorMappers: [
                    MapColorMapper(
                        from: 0,
                        to: 100,
                        color: Colors.red,
                        minOpacity: 0.2,
                        maxOpacity: 0.4),
                    MapColorMapper(
                        from: 101,
                        to: 300,
                        color: Colors.green,
                        minOpacity: 0.4,
                        maxOpacity: 0.6)
                  ]
              ),
            )
          ],
        ),
      ),
   );
}

class Model {
  const Model(this.country, this.count);

  final String country;
  final double count;
}

{% endhighlight %}
{% endtabs %}

![Shape color opacity](images/shape-colors/shape-color-opacity.png)

N>
* Refer the [`MapShapeLayerDelegate.bubbleColorMappers`](https://pub.dev/documentation/syncfusion_flutter_maps/latest/maps/MapShapeLayerDelegate/bubbleColorMappers.html), for setting the bubble colors based on the specific value.
