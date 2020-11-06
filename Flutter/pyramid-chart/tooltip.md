---
layout: post
title: Syncfusion Flutter Charts Tooltip
description: Learn how to enable and customize the tooltip options available in the Syncfusion Flutter Chart widget.
platform: flutter
control: Chart
documentation: ug
---

# Tooltip in Pyramid chart

Chart provides tooltip support for all the series. It is used to show information about the segment, when you tap on the segment. To enable the tooltip, you need to set [`enableTooltip`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/enableTooltip.html) property as *true*.

{% highlight dart %} 

    @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: Center(
            child: Container(
              child: SfPyramidChart(
                tooltipBehavior: TooltipBehavior(
                enable: true
                ),
                series: PyramidSeries<SalesData, String>(
                    dataSource: chartData,
                    xValueMapper: (SalesData sales, _) =>   sales.year,
                    yValueMapper: (SalesData sales, _) => sales.sales
                  )
              )
            )
          )
        );
      }

{% endhighlight %}

![Tooltip](images/tooltip/default_tooltip.png)

## Customizing the appearance

You can use the following properties to customize the tooltip appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/color.html) – used to change the background color of tooltip.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/borderWidth.html) – used to change the stroke width of the tooltip.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/borderColor.html) – used to change the stroke color of the tooltip.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/opacity.html) - used to control the transparency of the tooltip.
* [`duration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/duration.html) - specifies the duration for displaying the tooltip that defaults to 3000.
* [`animationDuration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/animationDuration.html) - specifies the duration for animating the tooltip that default to 350.
* [`elevation`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/elevation.html) - specifies the elevation of tooltip.
* [`canShowMarker`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/canShowMarker.html) - toggles the visibility of the marker in the tooltip.
* [`header`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/header.html) - specifies the header for tooltip. By default, the series name will be displayed in the header.
* [`format`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/format.html) - formats the tooltip text. By default, the tooltip will be rendered with x and y-values. You can add prefix or suffix to x, y, and series name values in the tooltip by formatting them.
* [`shadowColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/shadowColor.html) - specifies the color of the tooltip shadow.

{% highlight dart %} 

    @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: Center(
            child: Container(
              height: 350,
              width: 350,
              child: SfPyramidChart(
                tooltipBehavior: TooltipBehavior(
                enable: true,
                borderColor: Colors.red,
                borderWidth: 2,
                color: Colors.lightBlue
              ),
              )
            )
          )
        );
      }

{% endhighlight %}

![Customized tooltip](images/tooltip/customized_tooltip.png)

## Label format

By default, x and y value will be displayed in the tooltip, and it can be customized using [`format`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/format.html) property as depicted in the below code snippet. You can show the below values in the tooltip. Also you can add prefix or suffix to these values.

* X value - `point.x`
* Y value - `point.y`
* Bubble size - `point.size`
* Name of the series - `series.name`

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: Container(
            child: SfPyramidChart(
              tooltipBehavior: TooltipBehavior(
                enable: true, 
                // Formatting the tooltip text
                format: 'point.y%'
              )
            )
          )
        )
      );
    }

{% endhighlight %}

![tooltip format](images/tooltip/tooltip_format.png)

## Tooltip positioning

The tooltip can be made to display in the fixed location or at the pointer location itself using the `tooltipPosition` property. This defaults to `auto`.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: Container(
            child: SfPyramidChart(
              tooltipBehavior: TooltipBehavior(
                enable: true, 
                tooltipPosition: TooltipPosition.pointer
              )
            )
          )
        )
      );
    }

{% endhighlight %}

![pointer tooltip](images/tooltip/tooltip_pointer.png)

## Tooltip template

You can customize the appearance of the tooltip with your own widget by using the [`builder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/builder.html) property of [`tooltipBehavior`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart/tooltipBehavior.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: Container(
            child: SfPyramidChart(
              tooltipBehavior: TooltipBehavior(
                enable: true,
                // Templating the tooltip
                builder: (dynamic data, dynamic point, dynamic series,
                int pointIndex, int seriesIndex) {
                  return Container(
                    child: Text(
                      'Point Y : ${point.y.toString()}'
                    )
                  );
                }
              )
            )
          )
        )
      );
    }

{% endhighlight %}

![Tooltip template](images/tooltip/tooltip_template.png)

##	Activation mode

The [`activationMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/activationMode.html) property is used to restrict the visibility of tooltip based on the touch actions. The default value of this property is [`ActivationMode.singleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode-class.html).

The ActivationMode enum contains the following values:

* [`longPress`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode-class.html) – Activates tooltip only when performing the long press action.
* [`singleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode-class.html) – Activates tooltip only when performing single tap action.
* [`doubleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode-class.html) - Activates tooltip only when performing double tap action.
* [`none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode-class.html) – Hides the visibility of tooltip when setting activation mode to none.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: Container(
            child: SfPyramidChart(
              tooltipBehavior: TooltipBehavior(
                enable: true,
                // Tooltip will be displayed on long press
                activationMode: ActivationMode.longPress
              )
            )
          )
        )
      );
    }

{% endhighlight %}

Also refer [tooltip event](./events#ontooltiprender) for customizing the tooltip further.