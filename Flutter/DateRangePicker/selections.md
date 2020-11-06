---
layout: post
title: Selections in Syncfusion Flutter Date Range Picker | Syncfusion
description: This session describes the multiple selections in SfDateRangePicker widget in Flutter | DatePicker | Syncfusion
platform: Flutter
control: SfDateRangePicker
documentation: ug
---

# Selections in Flutter Date Range Picker (SfDateRangePicker)
Dates can be selected by touching the on month view cells. The default [selectionMode](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/selectionMode.html) is Single that allows the user to select one date at a time. `SfDateRangePicker` provides support to select dates in four modes such as `Single`, `Multiple`, `Range` and `MultiRange` selection

>**NOTE** When the `enableViewNavigation` property is set to false, the Date range picker allows you to select the cells in the year, decade, and century views of date range picker.

## Single selection
 A `single` date range picker cell can be selected in a date range picker view by setting the [DateRangePickerSelectionMode](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerSelectionMode-class.html) to `single`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.month,
       selectionMode: DateRangePickerSelectionMode.single,
       )
   );
}

{% endhighlight %}
{% endtabs %}

![SingleSelection Date Range Picker](images/selections/singleselection.jpg)

>**NOTE**
* The year, decade, and century view allow you to select cells only when the `enableViewNavigation` is set to false.
* In this scenario, the `selection changed` call back will return the first date of the month, year, or decade of the selected cell when the selection mode set to `single` and `multiple`.
Eg: 
* In the year view, when the May month cell is selected then the selected date value will be 01-05-2020.
* In the decade view, when the (2025) year cell is selected then the selected date value will be 01-01-2025.
* In the century view, when the (2020-2029) decade cell is selected then the selected date value will be 01-01-2020.


## Multiple selection
You can randomly select more than one date range picker cell by setting the `DateRangePickerSelectionMode` to `multiple`. By Clicking again you can deselect the selected cells.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.month,
       selectionMode: DateRangePickerSelectionMode.multiple,
       )
   );
}

{% endhighlight %}
{% endtabs %}

![MultiSelection Date Range Picker](images/selections/multiselection.jpg)

## Range selection
You can select a range of cells in any date range picker view by setting the `DateRangePickerSelectionMode` to the `range`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
               body: SfDateRangePicker(
               view: DateRangePickerView.month,
               selectionMode: DateRangePickerSelectionMode.range,
              )
      );
}

{% endhighlight %}
{% endtabs %}

![RangeSelection Date Range Picker](images/selections/range-selection.jpg)

>**NOTE**
* The year, decade, and century view allow you to select cells only when the `enableViewNavigation` set is as false.
* In this scenario, the `selection changed` call back will return the first and last date of the month, year, or decade of the selected cell when the selection mode is set to `range` and `multi-range`.
Eg: 
* In the year view, when the range is selected as May – June, then the range value will be 01-05-2020 to 30-06-2020.
* In the decade view, when the range is selected as 2025 – 2030, then the range value will be 01-01-2025 to 31-12-2030.
* In the century view, when the range is selected as 2020-2029 to 2030-2039, then the range value will be 01-01-2020 to 31-12-2039.


## Multi range selection
You can select more than one range of cells in any of the date range picker views by setting the `DateRangePickerSelectionMode` to the `multiRange`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
               body: SfDateRangePicker(
               view: DateRangePickerView.month,
               selectionMode: DateRangePickerSelectionMode.multiRange,
               )
      );
}

{% endhighlight %}
{% endtabs %}

![MultiRangeSelection Date Range Picker](images/selections/multirange.jpg)

## Selection radius
You can customize the radius of the selection using the [selectionRadius](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/selectionRadius.html) property of the `SfDateRangePicker`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      selectionRadius: 10,
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Selection radius Date Range Picker](images/selections/selectionradius.png)

## Selection shape
You can customize the selection shape of the selected date using the [selectionShape](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/selectionShape.html) property of the `DateRangePicker`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      selectionShape: DateRangePickerSelectionShape.rectangle,
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Selection shape Date Range Picker](images/selections/selectionshape.png)

## Enable swipe selection
Using the [enableSwipeSelection](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/enableSwipeSelection.html) property of the `DateRangePicker`, you can select the dates by using swiping. By default, `enableSwipeSelection` property as `true`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      selectionMode: DateRangePickerSelectionMode.range,
      monthViewSettings:
          DateRangePickerMonthViewSettings(enableSwipeSelection: false),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Toggle day selection
You can deselect the selected date using the [toggleDaySelection](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/toggleDaySelection.html) property of the `SfDateRangePicker`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      toggleDaySelection: true,
    ),
  );
}

{% endhighlight %}
{% endtabs %}