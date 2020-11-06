---
layout: post
title: Callbacks in Flutter Date Range Picker | Date Picker | Syncfusion
description: This session describes the Date Range Picker callbacks in the SfDateRangePicker widget in the Flutter.
platform: Flutter
control: SfDateRangePicker
documentation: ug
---

## Callbacks in Flutter date range picker
Calendar supports the `ViewChangedCallback` and `SelectionChangedCallback` to interact with the Flutter date range picker.

### View changed callback
The [onViewChanged](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/onViewChanged.html) callback triggers when the current view swiped to previous or next view, picker view switched to another picker view.

`visibleDateRange` - returns the start and end dates of the current visible month.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      onViewChanged: (DateRangePickerViewChangedArgs args) {
        var visibleDates = args.visibleDateRange;
      },
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Selection changed callback
The [onSelectionChanged](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/onSelectionChanged.html) callback triggers when selecting the dates from the date picker.

`args.value` - returns the dates based on the selection mode.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      selectionMode: DateRangePickerSelectionMode.range,
      onSelectionChanged: (DateRangePickerSelectionChangedArgs args) {
        if (args.value is PickerDateRange) {
          final DateTime rangeStartDate = args.value.startDate;
          final DateTime rangeEndDate = args.value.endDate;
        } else if (args.value is DateTime) {
          final DateTime selectedDate = args.value;
        } else if (args.value is List<DateTime>) {
          final List<DateTime> selectedDates = args.value;
        } else {
          final List<PickerDateRange> selectedRanges = args.value;
        }
      },
    ),
  );
}

{% endhighlight %}
{% endtabs %}
