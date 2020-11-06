---
layout: post
title: Callbacks in the Flutter Calendar | Scheduler | Syncfusion
description: Learn about the callbacks in Syncfusion Flutter Calendar and the return values and usage of the callbacks
platform: flutter
control: SfCalendar
documentation: ug
---

# Callbacks in flutter calendar
Calendar supports the [ViewChangedCallback](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/ViewChangedCallback.html) and [CalendarTapCallback](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTapCallback.html) to interact with Flutter calendar.

## View changed callback

The [onViewChanged](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onViewChanged.html) callback triggers when the current view of calendar changed, that is view swiped to previous /next view, calendar view switched to another calendar view.

`visibleDates` - returns the current view visible dates collection.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          onViewChanged: (ViewChangedDetails details) {
            dates = details.visibleDates;
          },
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

>**NOTE**
* Initially, the `onViewChanged` callback would be triggered to load the appointment data on the basis of visible dates.

## Calendar tap callback

The [onTapUp](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onTap.html) callback triggers whenever the calendar tapped.

`date` - returns the selected date.
`appointments` - returns the selected appointments.
`targetElement` - returns the element tapped.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          onTap: (CalendarTapDetails details) {
            appointment = details.appointments;
            date = details.date;
            element = details.targetElement;
          },
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Long press callback
The [onLongPress](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onLongPress.html) callback called whenever the `SfCalendar` elements long pressed on view.

The long-pressed date, appointments, and element details when the long-press action performed on element available in the [CalendarLongPressDetails](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarLongPressDetails-class.html).

`date` - returns the long-pressed date.
`appointments` - returns the long-pressed appointments.
`targetElement` - returns the long-pressed calendar element.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
            body: Container(
      child: SfCalendar(
        view: CalendarView.week,
        onLongPress: (CalendarLongPressDetails details) {
          DateTime date = details.date;
          dynamic appointments = details.appointments;
          CalendarElement view = details.targetElement;
        },
      ),
    )));
  }

{% endhighlight %}
{% endtabs %}

## See also

[How to get visible dates details from the flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/11026/how-to-get-visible-dates-details-from-the-flutter-event-calendar-sfcalendar)

[How to get Datetime details while tapping the Flutter event calendar elements](https://www.syncfusion.com/kb/10998/how-to-get-datetime-details-while-tapping-the-flutter-event-calendar-elements)

