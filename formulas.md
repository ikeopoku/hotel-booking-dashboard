# hotel-booking-dashboard

A Google Sheets-based to spot investment opportunity using financial and performance dashboard for hotel bookings







This document outlines the key formulas used in the \*\*Hotel Booking Dashboard (Google Sheets)\*\*. It includes data cleaning, modelling, and dashboard integration formulas to help understand and reproduce the logic.



---



\## 1. Data Cleaning Formulas



These formulas help sanitize raw input data and prepare it for analysis.



| Formula | Purpose |

|--------|---------|

| `=TEXT(B4, "MMMM")` | Convert date to full month name |

| `=TRIM(A2)` | Remove leading/trailing whitespace |

| `=CLEAN(A2)` | Remove non-printable characters |

| `=SUBSTITUTE(A1, ",", "")` | Remove commas or other unwanted characters |

| `=VALUE(A1)` | Convert text to numeric value |

| `=UPPER(A1)`, `=LOWER(A1)`, `=PROPER(A1)` | Normalize text casing |

| `=IFERROR(formula, "")` | Prevent formula errors from breaking output |

| `=UNIQUE(range)` | Return a list of unique values |

| `=ISNUMBER(A1)`, `=ISTEXT(A1)` | Validate data types |



---



\## 2. Data Modelling Formulas



These formulas transform cleaned data into meaningful metrics.



| Formula | Description |

|--------|-------------|

| `=VLOOKUP($J$1,'Monthly Expenses'!$U:$AJ, 16, FALSE)` | Lookup a specific hotel’s cost for a given month |

| `=SUMIFS('Daily Expenses'!E3:E273, 'Daily Expenses'!B3:B273, "January", 'Daily Expenses'!C3:C273, "Big Dreams Hotel")` | Sum values by multiple conditions |

| `=SUM(L19:L30)` | Total cost calculation |

| `=H8/E8` | Cap Rate = Net Operating Income / Cost |

| `=A9-B13` | Net Income = Rental Income - Total Cost |

| `=COUNTIF('2019'!R2:R9511, A3)` | Count matching values (e.g., visits by hotel) |

| `=INDEX(MATCH(...))` | Lookup values more flexibly than VLOOKUP |

| `=ROUND(value, 2)` | Round results for display/reporting |

| `=MONTH(A1)`, `=YEAR(A1)` | Extract date parts for grouping |

| `=IF(condition, true, false)` | Create conditional calculated fields |



---



\## 3. Dashboard & Display Formulas



These drive visual components and interactivity.



| Formula | Use Case |

|--------|----------|

| `=SORT(A3:B616, 2, FALSE)` | Sort hotel data by metric (e.g., visits or income) |

| `=UNIQUE('2019'!R2:R9511)` | Generate dropdown lists for hotel names |

| `=FILTER(range, condition)` | Show only matching data for dynamic charts |

| `=AVERAGE(range)`, `=MAX(range)`, `=MIN(range)` | Statistical summaries |

| `=SLOPE(Ys, Xs)`, `=INTERCEPT(Ys, Xs)` | For regression trendline (optional) |

| `=TEXT(A1, "0.00%")` | Format numbers as percentage |

| `=TEXT(A1, "$#,##0.00")` | Format as currency |



---



\## Extra Features Used



- **Named Ranges** – For cleaner references in formulas

- **Data Validation** – Dropdown for hotel selection (e.g., Cell `J1`)

- **Pivot Tables** – Summary tables by Hotel, Payment method, Rating.

- **Conditional Formatting** – Highlight negative income or high occupancy

- **Charts Used**:

- Line Chart → Monthly Net Income

- Donut Chart → Occupancy/Nights Rate

- Scatter Plot → Trendlines (Cap Rate vs Income, etc.)



---



\## Example Formula Breakdown



```=SUMIFS('Daily Expenses'!E3:E273, 'Daily Expenses'!B3:B273, "January", 'Daily Expenses'!C3:C273, "Big Dreams Hotel)



| Argument                                  	 | What It Does                                              	 |

| ---------------------------------------------- | --------------------------------------------------------------|

| `'Daily Expenses'!E3:E273`                	 | Range to sum (the actual expense amounts)             	 |

| `'Daily Expenses'!B3:B273, "January"`     	 | Only include rows where column B = "January"       	   	 |

| `'Daily Expenses'!C3:C273, "Big Dreams Hotel"` | Only include rows where column C = "Big Dreams Hotel"	 |



