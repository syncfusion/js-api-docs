---
layout: post
title: Localization of Syncfusion Flutter Date Range Picker | Date Picker
description: Describe how to Localize the contents in Syncfusion SfDateRangePicker widget in Flutter | Globalization | Internationalization | Date picker
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Localization in Flutter DateRangePicker (SfDateRangePicker)

By default, the calendar widget supports US English localizations. You can change other languages by specifying the `MaterialApp` properties and adding the `flutter_localizations` package to your application.

As of February 2020, [flutter package](https://flutter.dev/docs/development/accessibility-and-localization/internationalization) supports 77 languages.

To use `flutter_localizations`, add the package as a dependency to `pubspec.yaml` file.

{% highlight dart %}

dependencies:
flutter_localizations:
  sdk: flutter

{% endhighlight %}

Next, import the `flutter_localizations` library and specify `localizationsDelegates` and `supportedLocale` for `MaterialApp`.

{% tabs %}
{% highlight Dart %}

import 'package:flutter_localizations/flutter_localizations.dart';

@override
Widget build(BuildContext context) {
return MaterialApp(
        localizationsDelegates: [
            GlobalMaterialLocalizations.delegate,
            GlobalWidgetsLocalizations.delegate,
      ],
     supportedLocales: [
          const Locale('zh'),
          const Locale('ar'),
          const Locale('ja'),
      ],
      locale: const Locale('zh'),
      title: 'DateRangePicker Localization',
      home: Scaffold(
          appBar: AppBar(
          title: Text('Calendar'),
          ),
          body: SfDateRangePicker(
          view: DateRangePickerView.month,
           ),
       ),
   );
}

{% endhighlight %}
{% endtabs %}

![Localization Date Range Picker](images/localization/localization.png)
