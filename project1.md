---
layout: default
---

[Back to Portfolio](./)

Remote Job Scraper
===============

-   **Class: CSCI 301 Survey of Scripting Languages** 
-   **Grade: A** 
-   **Language(s): Python** 
-   **Source Code Repository:** [CSCI-301-code-repository](https://github.com/koimcf2005/CSCI-301-code-repository)  
    (Please [email me](mailto:kemcfarland@student.csuniv.edu?subject=GitHub%20Access) to request access.)

## Project description

This is a simple command-line remote-job scraper for https://remote.co.
It lets the user browse current remote job listings by category (e.g. Developer, Design, Marketing, Writing, etc.) and optionally filter them by a keyword and/or by job type (Full-time, Part-time, Freelance, Entry-level, High-paying, International).
For every matching job the script prints:
- Job title
- Company name
- Employment type badge (Full-time / Part-time / etc.)
- Posting date
- Salary (if the information is publicly shown on the job’s detail page)
- Direct link to the listing

The script is written in Python 3 and uses only two external libraries: requests and beautifulsoup4.

## How to run the program

Make sure you have Python 3.6+ installed.<br>
Install the required packages:

```bash
pip install requests beautifulsoup4
```

Then simply run it.

```bash
./remote_co_scraper.py
# or
python3 remote_co_scraper.py
```

## UI Design

This script provides a menu-driven terminal interface that guides the user through selecting a job category, an optional keyword filter, and an optional employment-type filter. After collecting input, the script retrieves matching job listings from *remote.co* and prints them in a structured format.

### Job Category Selection

When the script starts, it prints a list of numbered job categories:

```
Options:  
0 - Accounting, 1 - Customer Service, 2 - Data Entry, 3 - Design  
4 - Developer, 5 - Editing, 6 - Healthcare, 7 - HR  
8 - IT, 9 - Legal, 10 - Marketing, 11 - Project Manager  
12 - QA, 13 - Sales, 14 - Teaching, 15 - Virtual Assistant  
16 - Writing, 17 - Other  
```

The user is prompted with:

```
**Submit Job Type:**  
- Entering a valid number (0–17) selects the category.  
- Invalid input causes the program to print an error message and exit.
```

### Keyword Filter Input

Next, the user may optionally enter a keyword filter:

```
**Submit keyword to filter by (Press 'ENTER' for no keyword):**  
- ENTER = no keyword filter  
- Any text filters job titles by substring matching
```

### Employment Type Selection

The script then displays employment-type filter options:

```
Options:  
0 - Full-time, 1 - Part-time, 2 - Freelance  
3 - Entry-level, 4 - High-paying, 5 - International  
ENTER or any other key = no filter  
```

Prompt:

```
**Submit Hours:**  
- Entering 0–5 applies an hour-type filter.  
- ENTER or invalid input means no hour filtering.
```

### Job Listing Output

After scraping the listings, the script prints each matching job in a human-readable block:

```
[Job Title]:  
    Company: [Company Name]  
    [Employment Type]  
    Posted [Date]  
    Salary: [Value or "Not Posted"]  
    Link: https://remote.co/...  
```

For each job:  
- Titles are filtered by the optional keyword.  
- Employment type badges are filtered when selected.  
- Salary is pulled by loading each job’s detail page; if not available or shown as "$0", the script displays **Salary: Not Posted**.

### No Results Case

If no jobs match the selected filters, the script prints:

```
**No job listings were found with the given filters**
```

## Additional Considerations

- The script was written a couple of years ago. The HTML structure of remote.co may have changed since then, which could break the BeautifulSoup selectors (especially the salary extraction that opens every individual job page.

- Keyword matching is case-sensitive and looks only in the job title.

[Back to Portfolio](./)
