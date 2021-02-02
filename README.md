# NepaliCalendar

.NETCore Nuget packeage with collection of functions to work with Date in **Bikram Sambat (B.S.)**.

### Features:

* Convert BS dates to AD and vice versa
* Validate if the English dates & Nepali Dates are correct
* Converts Date in Bikram Sambat (B.S.) from **1970 B.S. to 2201 B.S**.

### Installation
NepaliCalendar requires .NET Core 2.0 +. Install it using the Nuget Manager or run the following command in Package Manager Console

$ Install-Package NepaliCalendar.NETCORE
Class & Methods available
The package has two class available. They are as follows:

### DateConverter
This class contains static methods which can be used to convert the dates. They are as follows:

### Method	Parameters	Description
ConvertToNepali	int Year, int Month, int day	This method is used to convert AD dates to BS.
ConvertToEnglish	int Year, int Month, int day	This method is used to convert BS dates to AD.
The above methods will return object with following property:

Variable	Description
Year	Converted Year
Month	Converted Month
Day	Converted Day
WeekDayName	Name of the day for the converted date
MonthName	Name of the month for the converted date
MonthName	Name of the month for the converted date
WeekDay	Week day number for the converted date
Calendar
This class contains methods to validate the dates. They are as follows:

Method	Parameters	Description
IsLeapYear	int Year	Returns in bool if the year is leap year or not.
GetDayOfWeek	int WeekDayNumber	Returns the name of the day of the week.
GetEnglishMonth	int Month Number	Returns the name of the english month for the provided month number.
GetNepaliMonth	int Month Number	Returns the name of the nepali month for the provided month number.
ValidEnglishDate	int Year, int Month, int day	Returns in bool if the enterted english date is valid or not
ValidNepaliDate	int Year, int Month, int day	Returns in bool if the enterted nepali date is valid or not
