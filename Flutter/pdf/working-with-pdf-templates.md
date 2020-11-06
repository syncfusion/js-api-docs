---
layout: post
title: Templates of Syncfusion Flutter PDF
description: Learn how to add templates in PDF document and add headers, footers and stamp with PDF templates by using the Syncfusion Flutter PDF.
platform: flutter
control: PDF
documentation: ug
---

# Working with PDF Templates

A PDF template is a drawing surface, where contents can be added. All the elements that can be added to a [`PdfPage`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPage-class.html) is supported in [`PdfTemplate`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfTemplate-class.html) as well. The template in turn can be drawn over the page or can be positioned at any part of the page.

## Creating a new PDF template

The [`PdfTemplate`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfTemplate-class.html) class can be used to create a new PDF template. You can add contents to the template using [`graphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPage/graphics.html) property of the [`PdfTemplate`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfTemplate-class.html) object.

The following code example explains how to add contents to the [`PdfTemplate`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfTemplate-class.html) and render into the new PDF page.

{% highlight dart %}

//Create a new PDF document.
PdfDocument document = PdfDocument();

//Create a PDF Template.
PdfTemplate template = PdfTemplate(100, 50);

//Draw a rectangle on the template graphics
template.graphics.drawRectangle(
    brush: PdfBrushes.burlyWood, bounds: Rect.fromLTWH(0, 0, 100, 50));

//Draw a string using the graphics of the template.
template.graphics.drawString(
    'Hello World', PdfStandardFont(PdfFontFamily.helvetica, 14),
    brush: PdfBrushes.black, bounds: Rect.fromLTWH(5, 5, 0, 0));

//Add a new page and draw the template on the page graphics of the document.
document.pages.add().graphics.drawPdfTemplate(template, Offset(0, 0));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(document.save());
document.dispose();

{% endhighlight %}

## Working with PdfPageTemplateElement

The [`PdfPageTemplateElement`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageTemplateElement-class.html) is a template element that can be added to any part of the PDF page such as header, footer, and more.

The following code example explains how to add the page template elements to a PDF document.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Add a page to the PDF document
PdfPage page = document.pages.add();

Rect bounds = Rect.fromLTWH(0, 0, page.getClientSize().width, 50);
PdfFont font = PdfStandardFont(PdfFontFamily.helvetica, 7);

//Create a header and draw the image
PdfPageTemplateElement header = PdfPageTemplateElement(bounds);

//Draw the image in the header
header.graphics.drawImage(
    PdfBitmap.fromBase64String(imageData),
    Rect.fromLTWH(0, 0, 100, 50));

//Add the header at the top
document.template.top = header;

//Create a Page template that can be used as footer
PdfPageTemplateElement footer = PdfPageTemplateElement(bounds);

//Add the fields in composite fields
PdfCompositeField compositeField = PdfCompositeField(
    font: font,
    brush: PdfBrushes.black,
    text: "Page {0} of {1}",
    fields: <PdfAutomaticField>[
      PdfPageNumberField(font: font, brush: PdfBrushes.black),
      PdfPageCountField(font: font, brush: PdfBrushes.black)
    ]);
compositeField.bounds = footer.bounds;

//Draw the composite field in footer
compositeField.draw(footer.graphics, Offset(470, 40));

//Add the footer template at the bottom
document.template.bottom = footer;

//Save and dispose the PDF document
File('SampleOutput.pdf').writeAsBytes(document.save());
document.dispose();

{% endhighlight %}

## Adding stamp to the PDF document

The Syncfusion Flutter PDF allows you add stamp to the PDF document using PDF templates.

The following code example explains how to draw text as a stamp to the PDF document.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Add a page to the PDF document
PdfPage page = document.pages.add();

//Create template and draw text in template graphics
final PdfPageTemplateElement custom =
    PdfPageTemplateElement(Offset(0, 0) & page.getClientSize(), page);
custom.dock = PdfDockStyle.fill;
PdfGraphicsState state = custom.graphics.save();
custom.graphics.rotateTransform(-40);
custom.graphics.drawString(
    'STAMP PDF DOCUMENT', PdfStandardFont(PdfFontFamily.helvetica, 20),
    pen: PdfPens.red,
    brush: PdfBrushes.red,
    bounds: Rect.fromLTWH(-150, 450, 400, 400));
custom.graphics.restore(state);

//Add template as a stamp to the PDF document
document.template.stamps.add(custom);

//Draw rectangle to the page graphics
page.graphics.drawRectangle(
    pen: PdfPen(PdfColor(0, 0, 0), width: 5),
    brush: PdfBrushes.lightGray,
    bounds: Offset(0, 0) & page.getClientSize());

//Save the document
final List<int> bytes = document.save();

//Dispose the document
document.dispose();

{% endhighlight %}