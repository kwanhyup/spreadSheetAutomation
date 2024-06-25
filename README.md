# spreadSheetAutomation

This project contains a Google Apps Script that automates certain tasks when specific values are edited in a Google Sheet. The script checks if a newly added value in "Sheet A" already exists in "Sheet B" and performs follow-up tasks automatically.

## Features

1. **Automated Status Marking**: 
   - When specific values ('valueA', 'valueB', or 'valueC') are entered in column N of "Sheet A", the script triggers automatic status updates and other tasks.
   
2. **Comparison with Sheet B**:
   - The script compares new entries in "Sheet A" with existing values in "Sheet B" to check for duplicates.
   
3. **Status Fixing**:
   - If a match is found, the script updates the status of the corresponding row in "Sheet A" and performs necessary updates on linked pages.

## How It Works

### Functions Overview

- `editColN(e)`: 
  - This function is triggered when a cell in "Sheet A" is edited. It checks if the edited cell is in column N and matches the specific values ('valueA', 'valueB', or 'valueC'). Based on the value, it calls the appropriate function for further processing.

- `statusMarkingBot(e)`:
  - This function updates the status of the target page if the edited value in column N is 'valueA' or 'valueB'. It then calls the `compareLink(e)` function.

- `compareLink(e)`:
  - This function compares the new link in column K of the edited row in "Sheet A" with the links in column K of "Sheet B". If a match is found, it calls the `fixTheStatus(e, matchingRow)` function with the matching row number.

- `fixTheStatus(e, matchingRow)`:
  - This function updates the status of the edited row in "Sheet A" and the corresponding linked page. It sets specific cell values in the edited row and updates the status of the page linked to the matched row in "Sheet B". It then calls the `setType(e)` function.

- `setType(e)`:
  - This function sets the type of the edited row in "Sheet A" to 'typeA'.

