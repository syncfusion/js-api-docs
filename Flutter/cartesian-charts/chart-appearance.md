---
layout: post
title: Customizing the appearance of Syncfusion Flutter Charts
description: Learn how to customize the appearance of SfCartesian Charts and the customizing properties available in SfCartesian charts.
platform: flutter
control: Chart
documentation: ug
---

# Appearance Of Cartesian charts

## Chart sizing

Chart renders based on the parent widget size. If you need the chart to be rendered in specific size, then set the size(width/height) to the parent widget.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              height: 300, // height of the Container widget
              width: 350,  // width of the Container widget
              child: SfCartesianChart()
            )
          )
        )
      );
    }

{% endhighlight %}

![Chart size](images/appearance/chart_sizing.jpg)

## Chart margin

Margin to the chart can be specified using the [`margin`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/margin.html) property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
        child: Container(
          height: 300, 
          width: 350, 
          child: SfCartesianChart(
              borderColor: Colors.red,
              borderWidth: 2,
              // Sets 15 logical pixels as margin for all the 4 sides.
              margin: EdgeInsets.all(15)
          )
        )
      );
    }

{% endhighlight %}

![Chart Margin](images/appearance/chart_margin.jpg)

## Plot area customization

You can customize the plot area of the chart using the below properties.

* [`plotAreaBackgroundColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/plotAreaBackgroundColor.html) – used to change the plot area background color.
* [`plotAreaBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/plotAreaBorderColor.html) – used to change the stroke width of the plot area.
* [`plotAreaBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/plotAreaBorderWidth.html) – used to change the stroke color of the plot area.
* [`plotAreaBackgroundImageUrl`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/plotAreaBackgroundImageUrl.html) - used to set the image path.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              height: 300, 
              width: 350, 
              child: SfCartesianChart(
                plotAreaBorderWidth: 5,
                plotAreaBorderColor: Colors.red,
                plotAreaBackgroundColor: Colors.lightGreen,
                plotAreaBackgroundImageUrl: 'images/livechart.png'
              )
            )
          )
        )
      );
    }

{% endhighlight %}

![Chart plot area](images/appearance/plot_area_customization.jpg)

## See Also

* [Rendering a background image in the plot area of the Cartesian chart](https://www.syncfusion.com/kb/11049/how-to-render-the-cartesian-chart-sfcartesianchart-with-background-image-for-plot-area).
* [Rendering the Cartesian chart in dark theme](https://www.syncfusion.com/kb/11025/how-to-render-the-flutter-cartesian-chart-sfcartesianchart-in-dark-theme).