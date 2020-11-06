---
layout: post
title: Localization in Syncfusion Flutter PDF Viewer | Syncfusion
description: This section explains about how to localize the contents and custom text elements in the Flutter PDF Viewer.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Localization in Flutter PDF Viewer (SfPdfViewer)

By default, the `SfPdfViewer` widget supports US English localization. You can change the other languages by specifying the `MaterialApp` properties and adding the `flutter_localizations` and `syncfusion_localizations` package to your application. 

To use `flutter_localizations` and `syncfusion_localizations`, add the packages as a dependency to the `pubspec.yaml` file.

{% highlight dart %}

dependencies:
flutter_localizations:
  sdk: flutter
syncfusion_localizations: ^XX.X.XX

{% endhighlight %}

Next, import the `flutter_localizations` and `syncfusion_localizations` library and specify the `localizationsDelegates` and `supportedLocales` for `MaterialApp` to localize the contents in the `SfPdfViewer` (page navigation dialog and bookmark view).

{% tabs %}
{% highlight Dart %}

import 'package:flutter_localizations/flutter_localizations.dart';
import 'package:syncfusion_localizations/syncfusion_localizations.dart';

@override
Widget build(BuildContext context) {
  return MaterialApp(
    localizationsDelegates: [
      GlobalMaterialLocalizations.delegate,
      GlobalWidgetsLocalizations.delegate, 
      SfGlobalLocalizations.delegate,
    ],
    supportedLocales: [
      const Locale('fr'),
      const Locale('ru'),
      const Locale('ta'),
    ],
    locale: const Locale('fr'),
    title: 'PDF Viewer Localization',
    home: Scaffold(
      appBar: AppBar(
        title: Text('Syncfusion Flutter PDF Viewer'),
      ),
      body: SfPdfViewer.network(
          'http://ebooks.syncfusion.com/downloads/flutter-succinctly/flutter-succinctly.pdf'),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Localization](images/localization/page_navigation_dialog_localization.png)