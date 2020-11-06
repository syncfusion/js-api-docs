---
layout: post
title: Bookmark navigation in Syncfusion Flutter PDF Viewer | Syncfusion
description: This section explains about how to navigate to the desired bookmark topics in the Flutter PDF Viewer.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Bookmark navigation in Flutter PDF Viewer (SfPdfViewer)

Navigate to the desired bookmark topics using the default bookmark view or the controller method programmatically.  

## Open and close the built-in bookmark view programmatically

The built-in bookmark view in the `SfPdfViewer` can be opened using the [openBookmarkView](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewerState/openBookmarkView.html) method and it can be closed either by tapping the close icon or device's back button. Also, we can close the bookmark programmatically by using the Navigator’s pop method. 

![Bookmark view](images/bookmark-navigation/bookmark_view.png)

The following code example explains the opening of built-in bookmark view programmatically.

{% tabs %}
{% highlight Dart %}

final GlobalKey<SfPdfViewerState> _pdfViewerKey = GlobalKey();

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('Syncfusion Flutter PdfViewer'),
      actions: <Widget>[
        IconButton(
          icon: Icon(
            Icons. bookmark,
            color: Colors.white,
          ),
          onPressed: () {
            _pdfViewerKey.currentState?.openBookmarkView();
          },
        ), 
      ],
    ),
    body: SfPdfViewer.network(
      'http://ebooks.syncfusion.com/downloads/flutter-succinctly/flutter-succinctly.pdf',
      key: _pdfViewerKey,
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Navigate to the desired bookmark topic programmatically

You can navigate to the desired bookmark topic programmatically using the [jumpToBookmark](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/jumpToBookmark.html) controller method. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

PdfViewerController _pdfViewerController;
PdfBookmark _pdfBookmark;

@override
void initState() {
  _pdfViewerController = PdfViewerController();
  super.initState();
}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      appBar: AppBar(
        title: Text('Syncfusion Flutter PdfViewer'),
        actions: <Widget>[
          IconButton(
            icon: Icon(
              Icons.arrow_drop_down_circle,
              color: Colors.white,
            ),
            onPressed: () {
              _pdfViewerController.jumpToBookmark(_pdfBookmark);
            },
          ),
        ],
      ),
      body: SfPdfViewer.network(
        'http://ebooks.syncfusion.com/downloads/flutter-succinctly/flutter-succinctly.pdf',
        controller: _pdfViewerController,
        onDocumentLoaded: (PdfDocumentLoadedDetails details) {
          _pdfBookmark = details.document.bookmarks[0];
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}