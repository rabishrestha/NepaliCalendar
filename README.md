# NepaliCalendarBS

.NETCore Nuget package with collection of functions to work with Date in **Bikram Sambat (B.S.)**.

### Features:

* Convert BS dates to AD and vice versa
* Validate if the English dates & Nepali Dates are correct
* Converts Date in Bikram Sambat (B.S.) from **1970 B.S. to 2201 B.S**.
* Generate an Array of CalendarDay[6,7] for given (Year, Month) B.S.

### Installation
NepaliCalendar is build on .NET Standard 2.0 so is compaitable to .NET Core 2.0 + or .NetFramework. Install it using the Nuget Manager.

### Class & Methods available
The package has one structure:
* **CalendarDay**
* WeekDay (Day of week i.e. 1->Sunday, 7->Saturday)
* int YearBS (Year in B.S.)
* int MonthBS (Month in B.S.)
* int DayBS (Day in B.S.)
* int YearAD (YearAD in A.D.)
* int MonthAD (MonthAD in A.D.)
* int DayAD (DayAD in A.D.)

The package has two class available. They are as follows:
* **NepaliDate**
* **NepaliCalendar**

### NepaliDate
Class to store Bikram Sambat Date. (B.S.) with following properties:
* int Year (Year in B.S.)
* int Month (Month in B.S.)
* int Day (Day in B.S.)
* WeekDay (Day of week i.e. 1->Sunday, 7->Saturday)

#### Functions
------------
* `public override string ToString()` 
Returns NepaliDate converted as string in format yyyy/MM/dd

* `public static int CompareTwoDates(NepaliDate Date1, NepaliDate Date2)` 
If Date1 (B.S.) is smaller returns -1, 0 for equal and 1 for greater

### NepaliCalendar
This class contains static methods which can be used to convert the dates. They are as follows:

------------

#### Functions
* `public static NepaliDate FixDate(string sDate)`
Converts Unicode Nepali numbers to english if necessary and returns valid B.S. date.
##### Parameters
Valid B.S. date in string
##### Returns
Date in B.S. in NepaliDate. If length of date == 10 returns same date else returns 1970/01/01 B.S.

* `public static string Get_Month_Name_Nepali(int iMonthInNumber)`
Gets first day of month as integer [Calendar Function]
##### Parameters
"**iYear**" (Integer year), "**iMonth**" (Integer from 1 to 12)
##### Returns
Integer value of total days in a month

* `public static NepaliDate TodayBS()`
Gets today B.S.
##### Returns
Date in Nepali Date format

* `public static string TodayBS_InLongString()`
Gets today B.S.
##### Returns
Date in Unicode Nepali Format (e.g. २०७७ साल श्रावण ३२ गते)

* `public static string CalculateAge(string sBSDate1, string sBSDate2, bool bInNepali)`
Calculates the date span (age) between two dates in Bikram Sambat (B.S.).
##### Parameters
"**sBSDate1**", "**sBSDate2**", "**bInNepali**"
##### Returns
Age in Year Month Day as string. If InNepali = true, बर्ष महिना दिन

* `public static int CalculateDaysFromRefYear(string sDateInBS)`
Calculates the no of days between 1970/01/01 B.S. and given date in B.S.
##### Parameters
"**sDateInBS**" (B.S. date in string, accepts Unicode Nepali and English)
##### Returns
Integer value for number of days

* `public static int CalculateDaysBetweenTwoBSDates(string sFirstDate, string sSecondDate)`
Calculates the no of days between given dates in B.S.
##### Parameters
"**sFirstDate**", "**sSecondDate**" (B.S. date in string, accepts Unicode Nepali and English)
##### Returns
Integer value for number of days

* `public static NepaliDate AddDaysInDateBS(string sDate, int iNoOfDays)`
Add some days in given date in B.S.
##### Parameters
"**sDate**", "**iNoOfDays**" (B.S. date in string, accepts Unicode Nepali and English)
##### Returns
New date in NepaliDate format

* `public static NepaliDate SubstractDaysInDateBS(string sDate, int iNoOfDays)`
Substracts some days from given date in B.S.
##### Parameters
"**sDate**", "**iNoOfDays**" (B.S. date in string, accepts Unicode Nepali and English)
##### Returns
New date in NepaliDate format

* `public static DateTime Convert_BS2AD(string sDateInBS)`
Converts date in B.S. to A.D.
##### Parameters
"**sDateInBS**" (B.S. date in string [e.g: **2077/01/01** OR **२०७७/०१/०१**], accepts Unicode Nepali and English)
##### Returns
New A.D. date in DateTime format

* `public static NepaliDate Convert_AD2BS(DateTime dtDateInAD)`
Converts date in A.D. to B.S.
##### Parameters
"**dtDateInAD**" -> A.D. Date in DateTime format
##### Returns
New B.S. date in NepaliDate format

* `public static CalendarDay[,] MakeCalendar(int iYearBS, int iMonthBS)`
Creates a calendar
##### Parameters
"**iYearBS**" -> Year in B.S.
"**iMonthBS**" -> Month in B.S.
##### Returns
An Array of CalendarDay[6,7]

------------
