# NepaliCalendarBS

.NETCore Nuget package with collection of functions to work with Date in **Bikram Sambat (B.S.)**.

### Features:

* Convert BS dates to AD and vice versa
* Validate if the English dates & Nepali Dates are correct
* Converts Date in Bikram Sambat (B.S.) from **1970 B.S. to 2201 B.S**.

### Installation
NepaliCalendar requires .NET Core 2.0 +. Install it using the Nuget Manager or run the following command in Package Manager Console

```sh
$ Install-Package NepaliCalendar.NETCORE
```

### Class & Methods available
The package has two class available. They are as follows:
* **NepaliDate**
* **NepaliCalendar**

### NepaliDate
Class to store Bikram Sambat Date. (B.S.) with following properties:
* int Year (Year in B.S.)
* int Month (Month in B.S.)
* int Day (Day in B.S.)
* WeekDay (Day of week i.e. 1->Sunday, 7->Saturday)

### NepaliCalendar
This class contains static methods which can be used to convert the dates. They are as follows:

------------

##### Function 
`public static NepaliDate FixDate(string sDate)`

##### Description
Converts Unicode Nepali numbers to english if necessary and returns valid B.S. date.
##### Parameters 
Valid B.S. date in string

##### Returns
Date in B.S. in NepaliDate. If length of date == 10 returns same date else returns 1970/01/01 B.S.

------------


