---
layout: post
title: Annotation in Syncfusion Circular Charts
description: Learn how to add and customize the Circular annotations available in the Syncfusion Circular Chart widget.
platform: flutter
control: Chart
documentation: ug
---

# Annotation in Circular charts

Chart supports annotations which allows you to mark the specific area of interest in the chart area. You can add the custom widgets using this annotations feature as depicted below.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              child: SfCircularChart(
                annotations: <CircularChartAnnotation>[
                  CircularChartAnnotation(
                    widget: 
                      Container(
                        child: const Text('Annotation')
                      ),
                  )
                ]
              )
            )
          )
        )
      );
    }

{% endhighlight %}

![Annotation](images/annotation/default_annotation.jpg)

## Positioning the annotation

The [`horizontalAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularChartAnnotation/horizontalAlignment.html) and [`verticalAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularChartAnnotation/verticalAlignment.html) values can be specified to align the annotation widget either horizontally or vertically, and the also the property [`radius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularChartAnnotation/radius.html) can be used for placing the annotation whose values range from '0%' to '100%'. Defaults to '0%'

**Positioning based on Alignment and Radius**

To Place the annotation based on the radius values, set the [`Radius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularChartAnnotation/radius.html), and for changing the alignment of the annotation use the [`horizontalAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularChartAnnotation/horizontalAlignment.html) and [`verticalAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularChartAnnotation/verticalAlignment.html) properties of annotation are shown in the following code snippet.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              child: SfCircularChart(
                annotations: <CircularChartAnnotation>[
                  CircularChartAnnotation(
                    widget: Container(
                      child: const Text('Text')
                    ),
                    radius: '50%',
                    verticalAlignment: ChartAlignment.center,
                    horizontalAlignment: ChartAlignment.far  
                ]
              )
            )
          )
        )
      );
    }

{% endhighlight %}

![Positioning based on Alignment and radius](images/annotation/annotation_positioning.jpg)

## Chart with watermark

Chart supports watermark which allows you to mark the specific area of interest in the chart area. You can add the custom widgets and watermarks using this annotations feature as depicted below.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SafeArea(
          child: Center(
            child: Container(
              child: SfCircularChart(
                annotations: <CircularChartAnnotation>[
                 CircularChartAnnotation(
                 child: Container(
                  child: const Text(
                    '€ - \$ ',
                  style: TextStyle(
                  color: Color.fromRGBO(216, 225, 227, 1),
                  fontWeight: FontWeight.bold,
                  fontSize: 80),
                    ),
                  ),
                 )
                ] 
              )
            )
          )
        )
      );
    }

{% endhighlight %}


![Chart with Watermark](images/annotation/watermark.jpg)