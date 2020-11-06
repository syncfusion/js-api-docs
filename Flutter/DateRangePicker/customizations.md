---
layout: post
title: Customizations Syncfusion Flutter Date Range Picker | Date Picker
description: Describe how to customize the Syncfusion SfDateRangePicker widget in Flutter | Date Picker | Customization
platform: Flutter
control: SfDateRangePicker
documentation: ug
---

# Customizations in Flutter DateRangePicker (SfDateRangePicker)

## Month cell customization
You can customize the calendar month view by using the `monthCellStyle` of `SfDateRangePicker`.

•    **Current month dates** – You can customize the current month date's text style and background of the `DateRangePicker` by using the [textStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/textStyle.html) and [cellDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/cellDecoration.html) properties of [DateRangePickerMonthCellStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle-class.html)

•    **Today date** – You can customize the today date text style and background of the `DateRangePicker` by using the [todayTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/todayTextStyle.html) and [todayCellDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/todayCellDecoration.html).

•    **Leading dates** – You can hide the leading dates by using the [showTrailingAndLeadingDates](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/showTrailingAndLeadingDates.html) property in the [DateRangePickerMonthViewSettings](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings-class.html) class. You can also customize the leading month dates text style and background of the `DateRangePicker` by using the [leadingDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/leadingDatesTextStyle.html) and [leadingDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/leadingDatesDecoration.html).

•    **Trailing dates** - You can hide the trailing dates by using `showTrailingAndLeadingDates` dates property in `DateRangePickerMonthViewSettings` class. You can also customize the trailing month dates text style and background of the `DateRangePicker` by using the [trailingDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/trailingDatesTextStyle.html) and  [trailingDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/trailingDatesDecoration.html).

•    **Blackout Dates** - You can customize the blackout dates text style and background of the `DateRangePicker` by using the [blackoutDateTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/blackoutDateTextStyle.html) and [blackoutDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/blackoutDatesDecoration.html).

•    **Disabled dates** – Disable dates text style and background beyond of the `minDate` and `maxDate` in `DateRangePicker` by using [disableDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/disabledDatesTextStyle.html) and  [disableDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/disabledDatesDecoration.html).

•    **Special Dates** – You can add special dates to the `DateRangePicker` by using [specialDates](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/specialDates.html) property, and you can also customize the special dates text style and background by using the [specialDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/specialDatesTextStyle.html) and [specialDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/specialDatesDecoration.html).

•    **Weekend Dates** – You can change weekend dates to `DateRangePicker` by using the [weekendDays](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/weekendDays.html) property, and you can also customize the weekend dates text style and background by using the [weekendDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/weekendTextStyle.html) and [weekendDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/weekendDatesDecoration.html).



{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.month,
       monthViewSettings:DateRangePickerMonthViewSettings(blackoutDates:List<DateTime>()
           ..add(DateTime(2020, 03, 26)),
      weekendDays: List<int>()
           ..add(7)..add(6),
      specialDates:List<DateTime>()
           ..add(DateTime(2020, 03, 20))..add(DateTime(2020, 03, 16))..add(DateTime(2020,03,17)),showTrailingAndLeadingDates: true),
      monthCellStyle: DateRangePickerMonthCellStyle(
         blackoutDatesDecoration: BoxDecoration(
               color: Colors.red,
               border: Border.all(color: const Color(0xFFF44436), width: 1),
               shape: BoxShape.circle),
        weekendDatesDecoration: BoxDecoration(
              color: const Color(0xFFDFDFDF),
              border: Border.all(color: const Color(0xFFB6B6B6), width: 1),
              shape: BoxShape.circle),
       specialDatesDecoration: BoxDecoration(
              color: Colors.green,
              border: Border.all(color: const Color(0xFF2B732F), width: 1),
              shape: BoxShape.circle),
       blackoutDateTextStyle: TextStyle(color: Colors.white, decoration: TextDecoration.lineThrough),
      specialDatesTextStyle: const TextStyle(color: Colors.white),
      ),
    )
  );
}

{% endhighlight %}
{% endtabs %}

![Customizations Date Range Picker](images/customizations/customizations.png)

## Month format
You can customize the month format of the `DateRangePicker` using the [monthFormat](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/monthFormat.html) property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      monthFormat: 'MMM',
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Month cell customization Date Range Picker](images/customizations/monthcell_customization.png)

## Selection cell customization

You can also customize the date range picker section by using the `monthCellStyle` of `SfDateRangePicker`.

•    **Selection date text style** – Selected date text style can be customized using the [selectionTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/selectionTextStyle.html) property of `SfDateRangePicker` that is applicable for `selectionMode` is `single` and `multiple`, it is also applicable to start and end of the selected range text style in the `single` and `multi-range` selection.

•    **Selection color** – Selected date background color can be customized using the [selectionColor](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/selectionColor.html) property of `SfDateRangePicker` that is applicable for `single` and `multiple` selections.

•    **Range selection text style** – Range selection date text style can be customized using the [rangeTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/rangeTextStyle.html) property that is applicable when `selectionMode` is `range` or `multi-range`.

•    **Range selection color** - Range selection color text style can be customized using the [startRangeSelectionColor](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/startRangeSelectionColor.html), [endRangeSelectionColor](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/endRangeSelectionColor.html) , [rangeSelectionColor](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/rangeSelectionColor.html)  properties that is applicable when `selectionMode` is in `range` or `multi-range`.

{% tabs %}
{% highlight Dart %}

@override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SfDateRangePicker(
      view: DateRangePickerView.month,
      selectionMode: DateRangePickerSelectionMode.range,
      selectionTextStyle: const TextStyle(color: Colors.white),
      selectionColor: Colors.blue,
      startRangeSelectionColor: Colors.purple,
      endRangeSelectionColor: Colors.purple,
      rangeSelectionColor: Colors.purpleAccent,
      rangeTextStyle: const TextStyle(color: Colors.white, fontSize: 20),
    ));
  }

{% endhighlight %}
{% endtabs %}

![Month Selection cell customization Date Range Picker](images/customizations/monthcell_selection_customization.png)

## Year cell customization
You can customize the calendar `year`, `decade`, and `century` view by using the `yearCellStyle` of `SfDateRangePicker`. 

•   **Current year** – You can customize current month dates text style and background of the `DateRangePicker` by using the [textStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/textStyle.html) and [cellDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/cellDecoration.html) properties of [DateRangePickerYearCellStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerYearCellStyle-class.html)

•   **Disabled dates** – Disable dates text style and background beyond of the `DateRangePicker` by using the [disableDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/disabledDatesTextStyle.html) and  [disableDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/disabledDatesDecoration.html).

•   **Leading dates** –  You can also customize the leading month dates text style and background of the `DateRangePicker` by using the [leadingDatesTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/leadingDatesTextStyle.html) and [leadingDatesDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/leadingDatesDecoration.html).

•   **Today date** – You can customize the today date text style and background of the `DateRangePicker` by using the [todayTextStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/todayTextStyle.html) and [todayCellDecoration](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthCellStyle/todayCellDecoration.html).

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
        body: SfDateRangePicker(
        view: DateRangePickerView.month,
        selectionMode: DateRangePickerSelectionMode.range,
        yearCellStyle: DateRangePickerYearCellStyle(
            disabledDatesDecoration:BoxDecoration(
                   color: const Color(0xFFDFDFDF),
                   border: Border.all(color: const Color(0xFFB6B6B6), width: 1),
                   shape: BoxShape.circle),
            disabledDatesTextStyle: const TextStyle(color: Colors.black),
            leadingDatesDecoration:BoxDecoration(
                   color: const Color(0xFFDFDFDF),
                   border: Border.all(color: const Color(0xFFB6B6B6), width: 1),
                   shape: BoxShape.circle),
            leadingDatesTextStyle: const TextStyle(color: Colors.black),
            textStyle: const TextStyle(color: Colors.blue),
            todayCellDecoration: BoxDecoration(
                   color: const Color(0xFFDFDFDF),
                   border: Border.all(color: const Color(0xFFB6B6B6), width: 1),
                   shape: BoxShape.circle),
           todayTextStyle: const TextStyle(color: Colors.purple),
           )
         ),
     );
}

{% endhighlight %}
{% endtabs %}

![Year cell customization Date Range Picker](images/customizations/yearcell_customization.png)

## See also

[How to customize the month cell of the Flutter date range picker (SfDateRangePicker)?](https://www.syncfusion.com/kb/11307/how-to-customize-the-month-cell-of-the-flutter-date-range-picker-sfdaterangepicker)