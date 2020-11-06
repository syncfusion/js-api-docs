---
layout: post
title: Date restrictions in Syncfusion Flutter Date Range Picker | Syncfusion
description: Learn about the complete date restriction in Syncfusion SfDateRangePicker widget in Flutter | Date Picker
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Date Restrictions in Flutter Date Range Picker (SfDateRangePicker)

## Minimum display date
The [minDate](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/minDate.html) will restrict `backward` date navigations features, and cannot swipe the control using the touch gesture beyond the min date range in all views.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
      view: DateRangePickerView.month,
      minDate: DateTime(2020, 03, 05, 10 , 0, 0),
     )
  );
}

{% endhighlight %}
{% endtabs %}

## Maximum display date
The [maxDate](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/maxDate.html) will restrict `forward` date navigations features, and cannot swipe the control using the touch gesture beyond the max date range in all views.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.month,
       maxDate: DateTime(2020, 03, 25, 10 , 0, 0),
       )
   );
}

{% endhighlight %}
{% endtabs %}

![Min_Max Date Date Range Picker](images/date-restrictions/min_max_date.png)

## Enable and disable past dates

The `DateRangePicker` allows you to enable or disable the past dates from today's date in `MonthView`. This can be achieved by changing the [enablePastDates](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/enablePastDates.html) property. By default, the value of this property is set to true.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.month,
       enablePastDates : false,
     )
   );
}

{% endhighlight %}
{% endtabs %}

![Enable and disable past dates Range Picker](images/date-restrictions/enable_diasable_pastdates.png)

## Blackout Dates
In `DateRangePicker`, [blackoutDates](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/blackoutDates.html) refer to the disabled dates that restrict the user from selecting it. These dates will be marked with Strikethrough.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.year,
       monthViewSettings: DateRangePickerMonthViewSettings(blackoutDates:List<DateTime>()
                ..add(DateTime(2020, 03, 18))..add(DateTime(2020, 03, 19))),
       )
   );
}

{% endhighlight %}
{% endtabs %}


