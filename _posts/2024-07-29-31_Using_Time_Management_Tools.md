---  
title: 31 Using Time Management Tools  
date: 2024-07-29 07:59:26 +0800  
categories: [emacs]  
tags: [emacs]  
---
## Displaying the Calendar

**M-x calendar**

By default, weeks start on Sunday. If you'd like them to start on Monday instead, type **M-x set-variable calendar-week-start Enter 1 Enter**. You enter the calendar again to have this take effect. If you'd like to have the calendar always start on Monday, add this line to your *.emacs* file:

```makefile
(setq calendar-week-start-day 1)
```

If you'd like to see the calendar each time you start Emacs, you can add this line to your *.emacs* file:

(calendar)

Calendar movement commands


| Keystrokes                                   | Command name                           | Action                                                |
| -------------------------------------------- | -------------------------------------- | ----------------------------------------------------- |
| **(none)** *Tools* **→** *Display Calendar* | **calendar**                           | Display the calendar.                                 |
| .*Goto* **→** *Today*                       | **calendar-goto-today**                | Move to today's date.                                 |
| **C-f**                                      | **calendar-forward-day**               | Move forward a day.                                   |
| **C-b**                                      | **calendar-backward-day**              | Move backward a day.                                  |
| **C-n**                                      | **calendar-forward-week**              | Move forward a week.                                  |
| **C-p**                                      | **calendar-backward-week**             | Move backward a week.                                 |
| **M-}**                                      | calendar-forward-month                 | Move forward one month.                               |
| **M-{**                                      | **calendar-backward-month**            | Move backward a month.                                |
| **C-x ]** *Scroll* **→** *Forward 1 Year*   | **calendar-forward-year**              | Move forward a year.                                  |
| **C-x [** *Scroll* **→** *Backward 1 Year*  | **calendar-backward-year**             | Move backward a year.                                 |
| **C-a** *Goto* **→** *Beginning of Week*    | **calendar-beginning-of-week**         | Move to the beginning of the week.                    |
| **C-e** *Goto* **→** *End of Week*          | **calendar-end-of-week**               | Move to the end of the week.                          |
| **M-a** *Goto* **→** *Beginning of Month*   | **calendar-beginning-of-month**        | Move to the beginning of the month.                   |
| **M-e** *Goto* **→** *End of Month*         | **calendar-end-of-month**              | Move to the end of the month.                         |
| **M-<** *Goto* **→** *Beginning of Year*    | **calendar-beginning-of-year**         | Move to the beginning of the year.                    |
| **M->** *Goto* **→** *End of Year*          | **calendar-end-of-year**               | Move to the end of the year.                          |
| **g d** *Goto* **→** *Other Date*           | **calendar-goto-date**                 | Go to the specified date.                             |
| **o**                                        | **calendar-other-month**               | Put the specified month in the middle of the display. |
| **C-x <** *Scroll* **→** *Forward 1 Month*  | **scroll-calendar-left**               | Scroll forward one month.                             |
| **C-x >** *Scroll* **→** *Backward 1 Month* | **scroll-calendar-right**              | Scroll backward one month.                            |
| **C-v** *Scroll* **→** *Forward 3 Months*   | **scroll-calendar-left-three-months**  | Scroll forward three months.                          |
| **M-v** *Scroll* **→** *Forward 3 Months*   | **scroll-calendar-right-three-months** | Scroll backward three months.                         |
| **Space**                                    | **scroll-other-window**                | Scroll another window.                                |

### Displaying holidays

To display the holidays for the part of the calendar you are looking at, type **a** (for **list-calendar-holidays**) or select **3 Months** from the **Holidays** menu.

want to see holidays surrounding the current month, type **M-x holidays**.

To see whether today is a holiday, type **h** or select **One Day** from the **Holidays** menu.

Typing **x** marks holidays in a special way; Typing **u** removes the marks.

We have taught you only the bare bones of the calendar commands. Emacs offers to tell you sunrise and sunset and phases of the moon. You can choose other calendars, like the Islamic calendar, the Hebrew calendar, the Mayan calendar, or even the French Revolutionary calendar. But we will leave these for you to explore.

## Using the Diary

### Creating a diary file

The file must be called *diary* and must exist in your home directory.The file must be called *diary*.

Here are a few lines from a *diary* file:

```bash
11/14 My birthday
July 17 2004 Company picnic
March 18 2004 Annual report due
January 8 2004 Hair appointment
&Saturday Tea with Queen Elizabeth
Friday Payday
```

If you don't specify a year, Emacs assumes you want to mark that date every year, as in birthdays;

If you don't specify a date but only the day of the week (as in tea with the queen on Saturday), Emacs displays the diary entry every Saturday;

Putting an ampersand (&) before an entry tells Emacs not to mark it on the calendar (you don't want every Saturday marked, and you may not want everyone to know that you hang around with the royal family).

To specify European date format, add this line to your *.emacs* file:

```.emacs
(setq european-calendar-style 't)
```

### **Adding diary entries**

If you want today's diary entries to display automatically when you start Emacs, add this line to your *.emacs* file:

```emacs
(diary)
```

To mark dates with diary entries in red, press **m** from the calendar. To remove the marks, press **u**. (This command removes highlighting for diary entries as well as for holidays.)

Table 5-5. Holiday and diary commands


| Keystrokes                                  | Command name                       | Action                                                                                 |
| ------------------------------------------- | ---------------------------------- | -------------------------------------------------------------------------------------- |
| **p d**                                     | **calendar-print-day-of-year**     | Display the day of the year this is (for example, Day 364 of 365).                     |
| **p o**                                     | **calendar-print-other-dates**     | Display information about this date for all calendars.                                 |
| **Space**                                   | **scroll-other-window**            | Scroll the other window.                                                               |
| **q**                                       | **exit-calendar**                  | Quit calendar.                                                                         |
| **a** *Holidays* **→** *For Window*        | **list-calendar-holidays**         | Display holidays for calendar period shown.                                            |
| **h** *Holidays* **→** *For Cursor Date*   | **calendar-cursor-holidays**       | In the minibuffer, display holiday information for the day the cursor is on.           |
| **x** *Holidays* **→** *Mark*              | **mark-calendar-holidays**         | Display holidays in a different typeface, color, or with an asterisk beside them.      |
| **u** *Holidays* **→** *Unmark Calendar*   | **calendar-unmark**                | Remove marks for holidays and diary entries (opposite of**x** command).                |
| **i w** *Diary* **→** *Insert Weekly*      | **insert-weekly-diary-entry**      | Add a weekly entry based on the day of the week.                                       |
| **i y** *Diary* **→** *Insert Yearly*      | **insert-yearly-diary-entry**      | Add an annual entry.                                                                   |
| **i d** *Diary* **→** *Insert Daily*       | **insert-diary-entry**             | Add an entry for a particular day.                                                     |
| **i m** *Diary* **→** *Insert Monthly*     | **insert-monthly-diary-entry**     | Add an entry for the day of the month.                                                 |
| **i c** *Diary* **→** *Insert Cyclic*      | **insert-cyclic-diary-entry**      | Add an entry to recur every*n* days.                                                   |
| **i a** *Diary* **→** *Insert Anniversary* | **insert-anniversary-diary-entry** | Add an annual entry (the year is included for reference).                              |
| **i b** *Diary* **→** *Insert Block*       | **insert-block-diary-entry**       | Add a block entry.                                                                     |
| **m**                                       | **mark-diary-entries**             | Display diary entries in a different typeface, color, or with a plus sign beside them. |
| **d**                                       | **view-diary-entries**             | Display diary entries for the current date.                                            |
| **s** *Diary* **→** *Show All*             | **show-all-diary-entries**         | Display*diary* file.                                                                   |
| **M-=**                                     | **calendar-count-days-region**     | Count the number of days in a region.                                                  |
| **M** *Moon* **→** *Lunar Phases*          | **calendar-phases-of-moon**        | Display phases of the moon for a three-month period.                                   |
| **S**                                       | **calendar-sunrise-sunset**        | Given longitude and latitude, display sunrise and sunset times for the current date.   |
| **C-Space** or **C-@**                      | **calendar-set-mark**              | Mark regions by time rather than horizontally.                                         |
