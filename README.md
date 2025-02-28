# CalendarDatePicker2

[![Pub Package](https://img.shields.io/badge/pub-v0.4.0-blue)](https://pub.dev/packages/calendar_date_picker2)
[![Pub Package](https://img.shields.io/badge/flutter-%3E%3D1.17.0-green)](https://flutter.dev/)

A lightweight and customizable calendar picker based on Flutter CalendarDatePicker, with support for single date picker, range picker and multi picker.

| ![single-mode-picker](https://user-images.githubusercontent.com/17869748/169690600-de51bee2-6f59-4f6a-95bf-c55e00dc54ae.gif) | ![multi-mode-picker](https://user-images.githubusercontent.com/17869748/169690730-e9cb5b29-8994-4e46-905e-83a14cc19809.gif) | ![range-picker-mode](https://user-images.githubusercontent.com/17869748/169690843-a7dc3fc2-0598-4050-aee0-e676d3a98c6c.gif) | ![dialog-function](https://user-images.githubusercontent.com/17869748/169691322-04404a63-53ff-4f90-a183-8d658806dedc.gif) |
| :--------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------: |
|                                                       **single mode**                                                        |                                                       **multi mode**                                                        |                                                       **range mode**                                                        |                                                    **dialog function**                                                    |

## Intro

CalendarDatePicker2 consists of two main widgets:

- `CalendarDatePicker2`, this widget only includes the calendar UI and will emit event whenever user taps a different date.
- `CalendarDatePicker2WithActionButtons`, this widget includes calendar UI and the action buttons (CANCEL & OK). This widget will only emit the updated value when user taps 'OK' button.

## Features

- Extended CalendarDatePicker allows `null` initialDate
- Highly Customizable UI
- Supports three modes: single, multi and range
- Built-in `showCalendarDatePicker2Dialog`

## How to use

Make sure to check out [examples](https://github.com/theideasaler/calendar_date_picker2/tree/main/example) for more details.

### Installation

Add the following line to `pubspec.yaml`:

```yaml
dependencies:
  calendar_date_picker2: ^0.4.0
```

### Basic setup

_The complete example is available [here](https://github.com/theideasaler/calendar_date_picker2/blob/main/example/lib/main.dart)._

**CalendarDatePicker2** requires you to provide `config` and `initialValue`:

- `config` contains the configurations for your calendar setup and UI.
- `initialValue` is initial values passed into your calendar picker, initial value must be a `List`.

### The minimum working sample

```dart
CalendarDatePicker2(
  config: CalendarDatePicker2Config(),
  initialValue: [],
);
```

### Single Date Picker Configuration

During the initialization of `CalendarDatePicker2Config` the `calendarType` of the config instance will by default set to `CalendarDatePicker2Type.single`, so you don't have to set the calendar type specifically.

### Multi Date Picker Configuration

In order to use multi mode date picker, you will need to set the calendarType of config to `CalendarDatePicker2Type.multi`:

```dart
CalendarDatePicker2(
  config: CalendarDatePicker2Config(
      calendarType: CalendarDatePicker2Type.multi,
  ),
  onValueChanged: (dates) => _yourHandler(dates),
  initialValue: [],
);
```

### Range Date Picker Configuration

In order to use range mode date picker, you will need to set the calendarType of config to `CalendarDatePicker2Type.range`:

```dart
CalendarDatePicker2(
  config: CalendarDatePicker2Config(
      calendarType: CalendarDatePicker2Type.range,
  ),
  onValueChanged: (dates) => _yourHandler(dates),
  initialValue: [],
);
```

### Use built-in dialog display method

This package includes built-in support to display calendar as a dialog. To use it, you will need to call `showCalendarDatePicker2Dialog`, which takes three required arguments: `context`, `config`, `dialogSize`:

```dart
...
var results = await showCalendarDatePicker2Dialog(
  context: context,
  config: CalendarDatePicker2WithActionButtonsConfig(),
  dialogSize: const Size(325, 400),
  initialValue: _dialogCalendarPickerValue,
  borderRadius: BorderRadius.circular(15),
);
...
```

### Config options

### For CalendarDatePicker2Config:

| Option                      | Type                           | Description                                                                         |
| --------------------------- | ------------------------------ | ----------------------------------------------------------------------------------- |
| calendarType                | CalendarDatePicker2Type?       | Calendar picker type, has 3 values: single, multi, range                            |
| firstDate                   | DateTime?                      | The earliest allowable DateTime user can select                                     |
| lastDate                    | DateTime?                      | The latest allowable DateTime user can select                                       |
| currentDate                 | DateTime?                      | The DateTime representing today which will be outlined in calendar                  |
| calendarViewMode            | DatePickerMode?                | The initially displayed view of the calendar picker                                 |
| weekdayLabels               | List\<String\>?                | Custom weekday labels, should starts with Sunday                                    |
| weekdayLabelTextStyle       | TextStyle?                     | Custom text style for weekday labels                                                |
| firstDayOfWeek              | int?                           | Index of the first day of week, where 0 points to Sunday, and 6 points to Saturday. |
| controlsHeight              | double?                        | Custom height for calendar control toggle's height                                  |
| lastMonthIcon               | Widget?                        | Custom icon for last month button control                                           |
| nextMonthIcon               | Widget?                        | Custom icon for next month button control                                           |
| controlsTextStyle           | TextStyle?                     | Custom text style for calendar mode toggle control                                  |
| dayTextStyle                | TextStyle?                     | Custom text style for calendar day text                                             |
| selectedDayTextStyle        | TextStyle?                     | Custom text style for selected calendar day text                                    |
| selectedDayHighlightColor   | Color?                         | The highlight color selected day                                                    |
| disabledDayTextStyle        | TextStyle?                     | Custom text style for disabled calendar day(s)                                      |
| todayTextStyle              | TextStyle?                     | Custom text style for current calendar day                                          |
| yearTextStyle               | TextStyle?                     | Custom text style for years list                                                    |
| selectedYearTextStyle       | TextStyle?                     | Custom text style for selected year                                                 |
| dayBorderRadius             | BorderRadius?                  | Custom border radius for day indicator                                              |
| yearBorderRadius            | BorderRadius?                  | Custom border radius for year indicator                                             |
| selectableDayPredicate      | SelectableDayPredicate?        | Function to provide full control over which dates in the calendar can be selected   |
| dayTextStylePredicate       | CalendarDayTextStylePredicate? | Function to provide full control over calendar days text style                      |
| dayBuilder                  | CalendarDayBuilder?            | Function to provide full control over day widget UI                                 |
| disableYearPicker           | bool?                          | Flag to disable year picker and hide the toggle icon                                |
| centerAlignModePickerButton | bool?                          | Flag to centralize year and month text label in controls                            |
| customModePickerButtonIcon  | Widget?                        | Custom icon for the mode picker button icon                                         |

### In addition to the configurations above, CalendarDatePicker2WithActionButtonsConfig has 9 extra options

| Option                       | Type        | Description                                     |
| ---------------------------- | ----------- | ----------------------------------------------- |
| gapBetweenCalendarAndButtons | double?     | The gap between calendar and action buttons     |
| cancelButtonTextStyle        | TextStyle?  | Text style for cancel button                    |
| cancelButton                 | Widget?     | Custom cancel button                            |
| okButtonTextStyle            | TextStyle?  | Text style for ok button                        |
| okButton                     | Widget?     | Custom ok button                                |
| openedFromDialog             | bool?       | Is the calendar opened from dialog              |
| closeDialogOnCancelTapped    | bool?       | Close dialog after user taps the CANCEL button  |
| closeDialogOnOkTapped        | bool?       | Close dialog after user taps the OK button      |
| buttonPadding                | EdgeInsets? | Custom wrapping padding for Ok & Cancel buttons |

### Custom UI

By using the configs above, you could make your own custom calendar picker as your need.

![image](https://user-images.githubusercontent.com/17869748/220879930-be9d981b-d7a6-44e9-b533-cb56e5733d90.png)

```dart
CalendarDatePicker2WithActionButtons(
  config: CalendarDatePicker2WithActionButtonsConfig(
    firstDayOfWeek: 1,
    calendarType: CalendarDatePicker2Type.range,
    selectedDayTextStyle: TextStyle(color: Colors.white, fontWeight: FontWeight.w700),
    selectedDayHighlightColor: Colors.purple[800],
    centerAlignModePickerButton: true,
    customModePickerButtonIcon: SizedBox(),
    dayBuilder: _yourDayBuilder,
  ),
  initialValue: _yourDatesVariable,
  onValueChanged: (dates) => setState(() => _yourDatesVariable = dates),
);
```

## Contributions

Feel free to contribute to this project. 🍺 Pull requests are welcome!

There are some tips before creating a PR:

- Please use the official [Dart Extension](https://marketplace.visualstudio.com/items?itemName=Dart-Code.dart-code) as your formatter or use `flutter format .` if you are not using VS Code
- Please keep your changes to its minimum needed scope (avoid introducing unrelated changes)
- Please follow this git commit [convention](https://www.conventionalcommits.org/en/v1.0.0-beta.2/) by adding `feat:` or `fix:` to your PR commit
