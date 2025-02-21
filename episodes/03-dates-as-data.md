---
title: Dates as Data
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Recognise problematic or suspicious date formats.
- Use formulas to separate dates into their component values (e.g., Year, Month, Day).

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- What are good approaches for handling dates in spreadsheets?

::::::::::::::::::::::::::::::::::::::::::::::::::

![](fig/onehalf_excel_meme.jpeg){alt="Meme with the text: Optimist: The glass is one-half full, Pessimist: The glass is one-half empyt, Excel: The glass is January 2nd."}

## Date formats in spreadsheets

Dates in spreadsheets are often stored in a single column.

While this seems like a logical way to record dates when you are entering them, or visually reviewing data, it's not actually a best practice for preparing data for analysis.

When working with data, your goal is to have as little ambiguity as possible. Ambiguity can creep into your data when working with dates when there are regional variations either in your observations or when you or your team might be working with different versions or suites of software products (e.g., LibreOffice, Microsoft Excel, Gnumeric).

To avoid ambiguity between regional differences in date formatting and compatibility across spreadsheet software programs, a good practice is to divide dates into components in different columns - YEAR, MONTH, and DAY.

When working with dates it's also important to remember that functions are guaranteed to be compatible only within the same family of software products (e.g., LibreOffice, Microsoft Excel, Gnumeric). If you need to export your data and conserve the timestamps, you are better off handling dates using one of the solutions discussed below than the single column method.

One of the other reasons dates can be tricky is that most spreadsheet programs have "useful features" which can change the way dates are displayed - but not stored. The image below demonstrates some of the many date formatting options in Excel.

![](fig/excel_dates_1.jpg){alt='Many formats, many ambiguities'}

Here is the official documentation for date formatting in [Microsoft Excel](https://support.microsoft.com/en-us/office/format-numbers-as-dates-or-times-418bd3fe-0577-47c8-8caa-b4d30c528309) and [LibreOffice Calc](https://wiki.documentfoundation.org/Videos/Format_date_in_Calc).

## Dates stored as integers

The first thing you need to know is that Excel stores dates as numbers - see the last column in the above figure. This serial number represents the number of days from December 31, 1899. In the example, July 2, 2014 is stored as the serial number 41822.

Using functions we can  add days, months or years to a given date.
Say you had a research plan where you needed to conduct interviews with a
set of informants every ninety days for a year.

In our example above, in a new cell you can  type:

\=B2+90

And it would return

30-Sep

because it understands the date as a number `41822`, and `41822 + 90 = 41912`
which Excel interprets as the 30th day of September, 2014. In most cases, it retains the format of the cell that is being operated upon. Month and year rollovers are internally tracked and applied.

## Regional date formatting

When you enter a date into a spreadsheet it looks like a date although the spreadsheet program may
display different text from what you input. It does this to be 'helpful' but it often is not.

For example if you enter '7/12/88' into your
Excel spreadsheet it may display as '07/12/1988' (depending on your version of Excel). These
are different ways of formatting the same date.

Different countries also write dates differently. If you are in the UK, for example, you will interpret
the date above as the 7th day of December, however a researcher from the US will interpret the same entry as the 12th day of July. This regional variation is handled automatically by your
spreadsheet program so that when you are typing in dates they appear as you would expect. If you
try to type in a US format date into a UK version of Excel, it may or may not be treated as a
date.

This regional variation is one good reason to treat dates, not as a single data point, but as
three distinct pieces of data (year, month, and day). Separating dates into their component parts
will avoid this confusion, while also giving the added benefit of allowing you to compare, for
example data collected in January of multiple years with data collected in February of multiple years.

:::::::::::::::::::::::::::::::::::::::  challenge

## Separating dates into components

Download and open the [SAFI\_dates.xlsx](https://ndownloader.figshare.com/files/11502827) file. This file
contains a subset of the data from the SAFI interviews, including the dates on which the
interviews were conducted.

Choose the tab of the spreadsheet that corresponds to the way you format dates in your
location (either day first `DD_MM_YEAR`, or month first `MM_DD_YEAR`).

Extract the components of the date to new columns. For this we
can use the built-in Excel functions:

`=YEAR()`  
`=MONTH()`  
`=DAY()`  

Apply each of these formulas to its entire column.
Make sure the new column is formatted as a number and not as a date.

We now have each component of our date isolated in its own column. This will allow us
to group our data with respect to year, month, or day of month for our analyses and will
also prevent problems when passing data between different versions of spreadsheet
software (as for example when sharing data with collaborators in different countries).

:::::::::::::::  solution

## Solution

![](fig/solution_exercise_1_dates.png){alt='dates exercise 1'}

Note that this solution shows the dates in `MM_DD_YEAR` format.



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Default year

Using the same spreadsheet you used for the previous exercise, add another data point
in the `interview_date` column by typing either `11/17` (if your location uses `MM/DD` formatting)
or `17/11` (if your location uses `DD/MM` formatting). The `Year`, `Month`, and `Day` columns
should populate for this new data point. What year is shown in the `Year` column?

:::::::::::::::  solution

## Solution

If no year is specified, the spreadsheet program will assume you mean the current year
and will insert that value. This may be incorrect if you are working with historical data so
be very cautious when working with data that does not have a year specified within its date
variable.



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Useful spreadsheet functions for working with date information

Let's take a look at some functions that will help us work with date information in spreadsheet applications.
Please remember that functions that are valid for a given
spreadsheet program (be it LibreOffice, Microsoft Excel, OpenOffice.org,
Gnumeric, etc.) are usually guaranteed to be compatible only within the same
family of products. So, if you will later need to export the data and need to
conserve the timestamps you should consider recording date information using one of the solutions discussed above.

If a date is entered in one column, we can use functions to extract information from that column into other columns. For example, it can be useful to display the specific information about the year, month, and day. Conversely, these functions can convert supplied numerical values from numbers into dates. Date-related functions allow us to convert date values from the stored numerical value to a readable display value, make calculations between date values, and also to extract the date values so that they do not change as data is transformed or exchanged between new users and systems.

The table below outlines a few useful date-related functions and how they differ between some of the widely used spreadsheet applications.

| Action of function                                                           | Excel | LibreOffice |
| ---------------------------------------------------------------------------- | ----- | ----------- |
| Return the year number represented in the referenced cell value              | `YEAR()`      | `YEAR()`            |
| Return the month number represented in the referenced date serial number     | `MONTH()`      | `MONTH()`            |
| Return the day of the month represented in the referenced date serial number | `DAY()`      | `DAY()`            |
| Calculate and display a date based on supplied year, month, and day values   | `DATE(Year, Month, Day)`      | `DATE(Year; Month; Day)`            |
| Return the serial number for date information supplied as a string           | `DATEVALUE("Text")`      | `DATEVALUE("Text")`            |
| Change display of a number by applying specified formatting                  | `TEXT(Value, "Formatting code to apply")`      | `TEXT(Value; "Formatting to apply")`            |
| Return the current system date                                               | `NOW()`      | `NOW()`            |


## Storing dates and times as a single string {#str}

When dealing with dates and times, the best alternative is to convert the date string
into a single string using the `YYYYMMDDhhmmss` format, following the international date standard [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601).
For example the date `March 24, 2015 17:25:35` would
become `20150324172535`, where:

```
YYYY:   the full year, i.e. 2015
MM:     the month, i.e. 03
DD:     the day of month, i.e. 24
hh:     hour of day, i.e. 17
mm:     minutes, i.e. 25
ss:     seconds, i.e. 35
```

Such strings will be correctly sorted in ascending or descending order, and by
knowing the format they can then be correctly processed by the receiving
software.

## Historical data

Excel is unable to parse dates from before 1899-12-31, and will thus leave these untouched.  If you're mixing historic data
from before and after this date, Excel will translate only the post-1900 dates into its internal format, thus resulting in mixed data. If you're working with historic data, be extremely careful with your dates!



:::::::::::::::::::::::::::::::::::::::: keypoints

- Use extreme caution when working with date data.
- Splitting dates into their component values can make them easier to handle.

::::::::::::::::::::::::::::::::::::::::::::::::::


