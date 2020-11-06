---
layout: post
title: Syncfusion Pyramid Chart Types
description: Learn how to add and customize the pyramid type of charts available in the Syncfusion Flutter Chart widget.
platform: flutter
control: Chart
documentation: ug
---

# Features of Pyramid chart

To render a pyramid chart, create an instance of [`PyramidSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/series.html) property of [`SfPyramidChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart-class.html). The following properties are used to customize the appearance of a pyramid segment.

* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/opacity.html) - Controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/borderWidth.html) – Changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/borderColor.html) – Changes the stroke color of the series.
* [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/pointColorMapper.html) - Maps the color from data source.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                            dataSource: [
                                ChartData('Walnuts', 654),
                                ChartData('Almonds', 575),
                                ChartData('Soybeans', 446),
                                ChartData('Black beans', 341),
                                ChartData('Mushrooms', 296),
                                ChartData('Avacado', 160),
                            ],
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y)
                    )
                )
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.y, [this.color]);
            final String x;
            final double y;
            final Color color;
    }

{% endhighlight %}

![Pyramid chart](images/pyramid-charts/pyramid.jpg)

## Pyramid modes

You can render the pyramid series as [`linear`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidMode-class.html) or [`surface`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidMode-class.html) mode. In linear mode, the height of the pyramid segment is based on the Y value, and in surface mode, area of the pyramid segment is based on the Y value. The default value of [`pyramidMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidMode-class.html) property is [`linear`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidMode-class.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                            pyramidMode: PyramidMode.surface
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Pyramid chart](images/pyramid-charts/pyramid_surface.jpg)

## Changing pyramid size

You can modify the size of pyramid series using the [`height`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/height.html) and [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/width.html) properties. It ranges from 0% to 100%.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                            height: '50%',
                            width: '50%',
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Pyramid size](images/pyramid-charts/pyramid_size.jpg)

## Gap between segments

You can control the gap between the two segments using the [`gapRatio`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/gapRatio.html) property. It ranges from 0 to 1.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                            gapRatio: 0.1,
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Pyramid gap](images/pyramid-charts/pyramid_gap.jpg)

## Explode segments

You can explode a pyramid segment using the [`explodeIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/explodeIndex.html) property. The [`explodeOffset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/explodeOffset.html) property is used to specify the exploded segment’s distance.

Also, the segments can be exploded by tapping the segment.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                            explode: true,
                            explodeOffset: '5%',
                            explodeIndex: 2,
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

![Explode](images/pyramid-charts/pyramid_explode.jpg)

## Smart data labels

The [`smartLabelMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/smartLabelMode.html) property is used to place the data labels smartly. The [`smartLabelMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/smartLabelMode.html) supports the following values:

* [`shift`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SmartLabelMode-class.html) - Shifts the data label position when a label intersects with other label.
* [`none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SmartLabelMode-class.html) - Renders all the data label when intersect.
* [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SmartLabelMode-class.html) - Hides the intersecting data label, and it is the default value.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        smartLabelMode: SmartLabelMode.shift,
                        series: PyramidSeries<ChartData, String>(
                            dataLabelSettings: DataLabelSettings(
                                isVisible: true, 
                                labelPosition: LabelPosition.inside
                            ),
                        )
                    )
                )
            )
        );
    }

{% endhighlight %}

## Applying palette color

The [`palette`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/palette.html) property is used to define colors for the series available in chart. By default, a set of 10 colors is predefined for applying it to the series. If the colors specified in the series are less than the number of series, then the remaining series will be filled with the specified palette colors rotationally.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        palette: <Color>[
                            Colors.teal,
                            Colors.orange,
                            Colors.brown
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Palette](images/pyramid-charts/pyramid_palette.jpg)
