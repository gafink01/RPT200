# RPT2000 - Year-To-Date Sales Report

## Table of Contents
1. [Overview](#overview)
2. [Author & Date](#author--date)
3. [Program Description](#program-description)
4. [Environment](#environment)
5. [Program Flow](#program-flow)

---

## Overview
**RPT2000** is a COBOL program designed to generate a Year-To-Date (YTD) sales report from a customer master file. The report lists individual customer sales for the current and previous year, calculates the change in sales amount and percentage, and displays grand totals for all qualifying customers. The program produces a formatted print report with page headings and totals.

---

## Author & Date
- **Programmer:** Garrett Finke  
- **Date:** 2026-02-25  

---

## Program Description
RPT2000 reads customer master records and produces a formatted Year-To-Date sales report. Key features include:

- Printing sales for each customer for the current and previous year.
- Calculating the change amount and percentage between the current and previous year's sales.
- Displaying grand totals for all customers with qualifying sales.
- Page numbering and date/time stamping on report headings.
- Only customers with `CM-SALES-THIS-YTD >= 10000` are included.

---

## Environment
- **Language:** COBOL  
- **File Format:** Fixed-length, 130 characters per record.  
- **Output:** Formatted report in 130-character lines.

---

## Report Layout
1. **Heading Lines:** Include date, time, program ID, and column headings.  
2. **Customer Lines:** Include branch, sales rep, customer number, customer name, current YTD sales, last YTD sales, change amount, and percentage.  
3. **Grand Totals:** Display totals for all qualifying customers with the same format as individual lines.  
4. **Page Breaks:** Automatically triggered when line count exceeds the page limit (55 lines by default).

---
## Program Flow

1. **Calculate Fields:**  
   - Compute `CHANGE-AMOUNT` = `CM-SALES-THIS-YTD - CM-SALES-LAST-YTD`.  
   - Compute `CHANGE-PERCENT` = `(CHANGE-AMOUNT * 100) / CM-SALES-LAST-YTD`.  
   - If last year’s sales are zero, `CHANGE-PERCENT` is set to `999.9`.

2. **Print Customer Lines:**  
   - Format each customer line and write to output.  
   - Update grand totals.  
   - Handle page breaks and headings.

3. **Print Grand Totals:**  
   - After all records are processed, compute and print grand totals.  
   - Display change amount and percentage for totals.

4. **Close Files:**  
   - Close input and output files.  
   - End program execution.

---

