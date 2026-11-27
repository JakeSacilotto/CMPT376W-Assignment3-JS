
# LogLens Setup and Installation Guide

This guide explains how to set up LogLens and run it for the first time. If you are unfamiliar with what LogLens does, see the [README](../README.md) for an overview of the program.

## Before You Begin

To set up LogLens, you will need:

- Python 3.10 or newer
- Access to a terminal

LogLens only uses the Python standard library, so no additional packages or `pip` installation are required.

## Setting Up LogLens

### 1. Check Your Python Version

Open your terminal and enter:

```bash
python --version
```

Make sure the version displayed is Python 3.10 or newer.

If the command does not work, try using `python3` or `py` instead. Use whichever Python command works on your computer for the remaining instructions.

### 2. Download the Project Files

From the [main page of the LogLens repository](../):

1. Click the green **Code** button.
2. Select **Download ZIP**.
3. Extract the ZIP file and locate the extracted folder using the command `cd`.

No further installation is required.

### 3. Open the Project Directory

Navigate to the extracted project folder in your terminal.

Before continuing, check that you are in the folder containing:

- The `loglens.py` file
- The `data` folder

This folder is called the repository root. All LogLens commands should be run from this location.

## Testing Your Setup

The repository includes a [sample CSV file](../data/sample_logs.csv) so you can check that LogLens is working before using your own files.

Run the following command to count all records in the sample file:

```bash
python loglens.py --file data/sample_logs.csv
```

Expected output:

```text
Records matching ALL: 6
```

Your output should match the expected output shown above.

You can also test whether the program counts records by log level:

```bash
python loglens.py --file data/sample_logs.csv --level ERROR
```

Expected output:

```text
Records matching ERROR: 2
```
If your command does not run successfully, see [Common Problems and Solutions](#common-problems-and-solutions).

## Using Your Own Log Files

Once you have tested LogLens with the sample file, you can use your own CSV files.

Before running the program, check that your CSV file contains the following exact column headers:

- `timestamp`
- `level`
- `message`

Make sure the log levels are written as `INFO`, `WARN`, or `ERROR`.

Replace `data/sample_logs.csv` in the previous commands with the path to your own CSV file.

For more examples and an explanation of the command-line arguments, see the [Using LogLens](../README.md#using-loglens) section of the README.

## Common Problems and Solutions

### Python Command Does Not Work

Check that Python 3.10 or newer is installed. Depending on your computer, you may need to use `python3` or `py` instead of `python`.

### File Not Found

Check the following before running the command again:

- Your terminal is in the repository root.
- The CSV file you are trying to read exists.
- The file path after `--file` is correct.

### Problems Reading the CSV File

Check that your CSV file uses the correct column headers and uppercase log levels.

**Incorrect CSV format:**

```csv
date,level,details
2026-01-03T09:00:00Z,info,Startup complete
```

**Correct CSV format:**

```csv
timestamp,level,message
2026-01-03T09:00:00Z,INFO,Startup complete
```

The first example uses incorrect column headers and a lowercase log level.

For more information, see the [Input File Format](../README.md#input-file-format) section of the README.

### Incorrect Arguments

If you are unsure which arguments to use, run:

```bash
python loglens.py --help
```

Remember that `--file` is required and `--level` is optional.

## Reporting an Issue

If you are still having trouble, you can open an issue on GitHub.

When reporting an issue:

- Describe the problem you are experiencing.
- Explain what you were trying to do when the problem occurred.
- Provide a small example with any sensitive information removed, if needed.

LogLens processes your files locally and does not upload or transmit them. Do not publicly share CSV files containing private or sensitive information.
