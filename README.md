# Owner-avatar-ITPM-Assignment01-IT23648272_SECOND_Option1

## Chat Translator Test Automation

This project contains an automated testing script (`IT23648272.py`) designed to validate the translation capabilities of the PixelsSuite Chat Translator. It reads test cases from an Excel file, inputs "Singlish" text into the web application, retrieves the translated "Sinhala" output, and compares it against expected results to determine a PASS or FAIL status.

## Prerequisites

- Python 3.8 or higher
- [Playwright](https://playwright.dev/python/) (for browser automation)
- [openpyxl](https://openpyxl.readthedocs.io/) (for reading and writing Excel files)

## Project Structure

- `IT23648272.py` - The main Python script that runs the Playwright automation.
- `IT23648272.xlsx` - An example Excel file containing the test cases (Input, Expected Output, etc.).
- `venv/` - A Python virtual environment.

## Setup Instructions

1. **Activate the Virtual Environment:**
   - On macOS/Linux:
     ```bash
     source venv/bin/activate
     ```
   - On Windows:
     ```bash
     venv\Scripts\activate
     ```

2. **Install Dependencies:**
   Ensure you have the required libraries installed in your virtual environment:
   ```bash
   pip install playwright openpyxl
   ```

3. **Install Playwright Browsers:**
   Download the Chromium browser required by Playwright to run the tests:
   ```bash
   playwright install chromium
   ```

## Running the Tests

To execute the automated test script, simply run the following command in your terminal:

```bash
python IT23648272.py --excel IT23648272.xlsx
```

### Additional Command Line Arguments

You can customize the test execution by providing optional arguments:

- `--excel <path>`: Path to the Excel file containing test cases (Default searches for `Assignment 1 - Test cases.xlsx`).
- `--sheet <name>`: Specific sheet name to use within the Excel file.
- `--headless`: Run the browser in headless mode (no UI). Useful for faster execution.
- `--url <url>`: The target frontend URL to test (Default: `https://www.pixelssuite.com/chat-translator`).
- `--output <path>`: Custom path to save the resulting Excel file after tests are completed.
- `--timeout-ms <ms>`: Maximum timeout for page loads and element selection (Default: 60000ms).
- `--slow-mo-ms <ms>`: Slows down Playwright operations by the specified amount of milliseconds. Useful for observing the test execution.

**Example with arguments:**
```bash
python IT23648272.py --excel IT23648272.xlsx --headless --timeout-ms 30000
```

## How It Works

1. **Initialization:** The script loads the specified Excel file and identifies the appropriate columns for input, expected output, actual output, and status.
2. **Browser Launch:** It launches a Playwright Chromium browser instance and navigates to the Chat Translator web app.
3. **Execution:** For each row in the Excel sheet, it inputs the 'Singlish' text, clicks the translation button (or waits for auto-translation), and reads the 'Sinhala' output.
4. **Validation:** It compares the actual output with the expected output and marks the row's status as `PASS` or `FAIL`.
5. **Saving:** Once all test cases are executed, the script updates the Excel file with the results.