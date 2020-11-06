---
layout: post
title: Excel worksheet of Syncfusion Flutter XlsIO.
description: Learn how to create and access a worksheet of workbook and manipulating the worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Working with Excel Worksheets

A Workbook contains a collection of worksheets where the actual contents reside and Worksheet instance represents a worksheet. With Flutter XlsIO, you can add and manipulate worksheets.

## Create a Worksheet

You can add a new worksheet into the Workbook through instances of workbook. You can also specify the required number of worksheets, if not specified, Flutter XlsIO will create one worksheet by default.

The following code snippet shows how to create worksheets within a workbook.

{% highlight dart %}

// The new workbook will have 4 worksheets.
final Workbook workbook = Workbook(4);

// Creating a Sheet.
final Worksheet sheet = Worksheet(workbook);
workbook.worksheets.addWithSheet(sheet);

//Creating a Sheet with name “Sample”.
final Worksheet sheet1 = workbook.worksheets.addWithName('Sample');

// Add worksheet to the collection.
final Worksheet sheet2 = workbook.worksheets.add();

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Access a Worksheet

Worksheets collection holds one or more worksheets present in a workbook. Accessing a particular worksheet can be done by the following ways.

1. Specifying the index
2. Specifying the sheet name.

The below codes illustrate how to access a worksheet from its worksheets collection.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();
workbook.worksheets.addWithName('sample');

// Accessing via index. 
final Worksheet sheet = workbook.worksheets[0]; 

//Accessing via sheet Name. 
final Worksheet namedSheet = workbook.worksheets['Sample'];

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## View Settings

**Show or Hide Grid Lines**

The following code snippet shows how to hide the grid lines using **showGridLines** property.

{% highlight dart %}

//Create a new Excel Document.
final Workbook workbook = Workbook();

//Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Hide grid line.
sheet.showGridLines = false;

//Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Adjust Row Height and Column Width

**Resize a range of rows or columns**

Single/Multiple rows or columns can be resized and accessed by using the **rowHeight** and **columnWidth** properties of **Range**. The following code snippet shows how to resize single/multiple rows and columns.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Modifying the row height for single and multiple range.
sheet.getRangeByName('A1').rowHeight = 10;
sheet.getRangeByName('A2:A5').rowHeight = 20;

// Modifying the columnWidth for single and multiple range.
sheet.getRangeByName('A1').columnWidth = 20;
sheet.getRangeByName('A2:A5').columnWidth = 30;

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

