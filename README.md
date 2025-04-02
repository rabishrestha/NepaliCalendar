# NepaliCalendarBS

A .NET Core NuGet package providing a robust set of utilities for working with dates in the **Bikram Sambat (B.S.)** calendar system, commonly used in Nepal.

## Features
- Convert dates between Bikram Sambat (B.S.) and Anno Domini (A.D.) systems.
- Validate both English (A.D.) and Nepali (B.S.) dates for correctness.
- Supports B.S. dates from **1970 B.S. to 2201 B.S.**.
- Generate a calendar array (CalendarDay[6,7]) for a given B.S. year and month.
- Format B.S. dates in multiple styles, including Nepali Unicode and English.

## Installation
NepaliCalendarBS is built on **.NET Standard 2.0**, making it compatible with **.NET Core 2.0+** and **.NET Framework 4.6.1+**. Install it via NuGet Package Manager:

bash
dotnet add package NepaliCalendarBS

## Classes and Structures
The package includes one structure and two classes:

### CalendarDay Structure
Represents a single day in the calendar with both B.S. and A.D. components.

- **Properties**:
  - int? WeekDay: Day of the week (1 = Sunday, 7 = Saturday).
  - int? YearBS: Year in B.S.
  - int? MonthBS: Month in B.S.
  - int? DayBS: Day in B.S.
  - int? YearAD: Year in A.D.
  - int? MonthAD: Month in A.D.
  - int? DayAD: Day in A.D.

### NepaliDate Class
A class to store and manipulate Bikram Sambat (B.S.) dates.

- **Properties**:
  - int Year: Year in B.S.
  - int Month: Month in B.S. (1–12).
  - int Day: Day in B.S.
  - int WeekDay: Day of the week (1 = Sunday, 7 = Saturday; read-only, calculated).

#### Methods
- **public string ToString(string format = null)**
  - **Description**: Converts the NepaliDate to a string in the specified format.
  - **Parameters**:
    - format (optional):
      - "nepali": Nepali long format (e.g., "२०८१ बैशाख १ गते").
      - "english": English format (e.g., "2081 Baishak 1").
      - "nepali_short": Nepali short format (e.g., "२०८१/०१/०१").
      - Default (null): Standard format (e.g., "2081/01/01").
  - **Returns**: A string representation of the date. Returns an empty string if the date is 1970/01/01.
  - **Example**:
    csharp
    var date = new NepaliDate(2081, 1, 1);
    Console.WriteLine(date.ToString());          // "2081/01/01"
    Console.WriteLine(date.ToString("nepali"));  // "२०८१ बैशाख १ गते"
    Console.WriteLine(date.ToString("english")); // "2081 Baishak 1"
    Console.WriteLine(date.ToString("nepali_short")); // "२०८१/०१/०१"
    

- **public override string ToString()**
  - **Description**: Default string representation (calls ToString(null)).
  - **Returns**: Date in "yyyy/MM/dd" format (e.g., "2081/01/01"), or an empty string if 1970/01/01.

- **public static int CompareTwoDates(NepaliDate Date1, NepaliDate Date2)**
  - **Description**: Compares two B.S. dates.
  - **Parameters**:
    - Date1: First NepaliDate.
    - Date2: Second NepaliDate.
  - **Returns**:
    - -1 if Date1 < Date2.
    - 0 if Date1 == Date2.
    - 1 if Date1 > Date2.
  - **Example**:
    csharp
    var date1 = new NepaliDate(2081, 1, 1);
    var date2 = new NepaliDate(2081, 1, 2);
    Console.WriteLine(NepaliDate.CompareTwoDates(date1, date2)); // -1
    

### NepaliCalendar Class
A static utility class for B.S. date operations and conversions.

#### Methods
- **public static NepaliDate FixDate(string sDate)**
  - **Description**: Validates and normalizes a B.S. date string, converting Nepali Unicode numbers to English if needed.
  - **Parameters**:
    - sDate: B.S. date string (e.g., "2081/01/01" or "२०८१/०१/०१").
  - **Returns**: A NepaliDate object. Returns 1970/01/01 if invalid or length ≠ 10.
  - **Example**:
    csharp
    var date = NepaliCalendar.FixDate("२०८१/०१/०१");
    Console.WriteLine(date.ToString()); // "2081/01/01"
    

- **public static string Get_Month_Name_Nepali(int iMonthInNumber)**
  - **Description**: Returns the Nepali name of a month.
  - **Parameters**:
    - iMonthInNumber: Month number (0–12; 0 = "-सबै-", 1–12 = month names).
  - **Returns**: Unicode Nepali month name (e.g., "बैशाख" for 1).
  - **Example**:
    csharp
    Console.WriteLine(NepaliCalendar.Get_Month_Name_Nepali(1)); // "बैशाख"
    

- **public static NepaliDate TodayBS()**
  - **Description**: Gets the current date in B.S.
  - **Returns**: A NepaliDate representing today’s date in B.S.
  - **Example**:
    csharp
    var today = NepaliCalendar.TodayBS();
    Console.WriteLine(today.ToString("nepali")); // e.g., "२०८१ चैत्र १९ गते"
    

- **public static string TodayBS_InLongString()**
  - **Description**: Gets today’s date in a long Nepali format.
  - **Returns**: Unicode Nepali string (e.g., "२०८१ साल चैत्र १९ गते").
  - **Example**:
    csharp
    Console.WriteLine(NepaliCalendar.TodayBS_InLongString()); // e.g., "२०८१ साल चैत्र १९ गते"
    

- **public static string CalculateAge(string sBSDate1, string sBSDate2, bool bInNepali)**
  - **Description**: Calculates the age between two B.S. dates.
  - **Parameters**:
    - sBSDate1: Start date (B.S. string).
    - sBSDate2: End date (B.S. string).
    - bInNepali: true for Nepali output, false for English.
  - **Returns**: Age as a string (e.g., "5 बर्ष 2 महिना 3 दिन" or "5 Year 2 Month 3 Day").
  - **Example**:
    csharp
    var age = NepaliCalendar.CalculateAge("2076/01/01", "2081/01/01", true);
    Console.WriteLine(age); // "५ बर्ष ० महिना ० दिन"
    

- **public static int CalculateDaysFromRefYear(string sDateInBS)**
  - **Description**: Calculates days from 1970/01/01 B.S. to the given date.
  - **Parameters**:
    - sDateInBS: B.S. date string.
  - **Returns**: Number of days as an integer.
  - **Example**:
    csharp
    Console.WriteLine(NepaliCalendar.CalculateDaysFromRefYear("2081/01/01")); // e.g., 4086
    

- **public static int CalculateDaysBetweenTwoBSDates(string sFirstDate, string sSecondDate)**
  - **Description**: Calculates the number of days between two B.S. dates.
  - **Parameters**:
    - sFirstDate: First B.S. date string.
    - sSecondDate: Second B.S. date string.
  - **Returns**: Number of days as an integer.
  - **Example**:
    csharp
    Console.WriteLine(NepaliCalendar.CalculateDaysBetweenTwoBSDates("2081/01/01", "2081/01/02")); // 1
    

- **public static NepaliDate AddDaysInDateBS(string sDate, int iNoOfDays)**
  - **Description**: Adds days to a B.S. date.
  - **Parameters**:
    - sDate: B.S. date string.
    - iNoOfDays: Number of days to add.
  - **Returns**: New NepaliDate.
  - **Example**:
    csharp
    var newDate = NepaliCalendar.AddDaysInDateBS("2081/01/01", 10);
    Console.WriteLine(newDate.ToString()); // "2081/01/11"
    

- **public static NepaliDate SubstractDaysInDateBS(string sDate, int iNoOfDays)**
  - **Description**: Subtracts days from a B.S. date.
  - **Parameters**:
    - sDate: B.S. date string.
    - iNoOfDays: Number of days to subtract.
  - **Returns**: New NepaliDate.
  - **Example**:
    csharp
    var newDate = NepaliCalendar.SubstractDaysInDateBS("2081/01/11", 10);
    Console.WriteLine(newDate.ToString()); // "2081/01/01"
    

- **public static DateTime Convert_BS2AD(string sDateInBS)**
  - **Description**: Converts a B.S. date to A.D.
  - **Parameters**:
    - sDateInBS: B.S. date string (e.g., "2081/01/01" or "२०८१/०१/०१").
  - **Returns**: A DateTime object in A.D.
  - **Example**:
    csharp
    var adDate = NepaliCalendar.Convert_BS2AD("2081/01/01");
    Console.WriteLine(adDate.ToString("yyyy-MM-dd")); // "2024-04-14"
    

- **public static NepaliDate Convert_AD2BS(DateTime dtDateInAD)**
  - **Description**: Converts an A.D. date to B.S.
  - **Parameters**:
    - dtDateInAD: A.D. date as a DateTime.
  - **Returns**: A NepaliDate object in B.S.
  - **Example**:
    csharp
    var bsDate = NepaliCalendar.Convert_AD2BS(new DateTime(2024, 4, 14));
    Console.WriteLine(bsDate.ToString()); // "2081/01/01"
    

- **public static CalendarDay[,] MakeCalendar(int iYearBS, int iMonthBS)**
  - **Description**: Generates a 6x7 calendar array for a B.S. month.
  - **Parameters**:
    - iYearBS: Year in B.S.
    - iMonthBS: Month in B.S. (1–12).
  - **Returns**: A CalendarDay[6,7] array.
  - **Example**:
    csharp
    var calendar = NepaliCalendar.MakeCalendar(2081, 1);
    Console.WriteLine(calendar[0, 0].DayBS); // First Sunday’s day in Baishak 2081
    

## Notes
- All methods handle both English and Nepali Unicode date inputs where applicable.
- The package assumes Nepal Standard Time (UTC+5:45) for current date calculations.
- Ensure input dates fall within the supported range (1970–2201 B.S.).

## Contributing
Feel free to submit issues or pull requests to the [GitHub repository](https://github.com/your-repo) to enhance functionality or fix bugs.
