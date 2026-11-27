
# LogLens

LogLens is a local, command-line Python program that counts records in CSV log files. You can count all records in a CSV file or count records by log level.

LogLens is intended for undergraduate computing students and new technical interns who have a basic understanding of CSV files and experience using a terminal.

## Requirements

To use LogLens, you will need:

- Python 3.10 or newer
- A copy of the LogLens repository
- A CSV log file that follows the [required input format](#input-file-format)

LogLens uses only the Python standard library. No additional dependencies or `pip` installation are required.

## Getting Started

Follow the [Installation Guide](docs/INSTALL.md) to download and set up LogLens.

Before running any commands, make sure your terminal is in the repository root, which is the directory containing `loglens.py`.

The following examples use `python`. Depending on your computer, you may need to use `python3` or `py` instead.

## Using LogLens

The repository includes a [sample CSV file](data/sample_logs.csv) that you can use to test the program.

LogLens uses two command-line arguments:

- `--file` (required): Tells LogLens which CSV file to read.
- `--level` (optional): Tells Loglens which log level to count (`INFO`, `WARN`, or `ERROR`). If left out, all records in the CSV file will be counted.
  
 When using your own CSV file, replace `data/sample_logs.csv` in the examples below with the path to your file.

### Count Records by Log Level

To count the number of records with the `ERROR` log level, run:

```bash
python loglens.py --file data/sample_logs.csv --level ERROR
```

Expected output:

```text
Records matching ERROR: 2
```

### Count All Records

To count all records in the CSV file, run the command without the `--level` argument:

```bash
python loglens.py --file data/sample_logs.csv
```

Expected output:

```text
Records matching ALL: 6
```

### View Available Arguments

To view the available arguments, run:

```bash
python loglens.py --help
```

## Input File Format

LogLens requires a CSV file with the following exact column headers:

- `timestamp`: The date and time of the log entry.
- `level`: The log level (`INFO`, `WARN`, or `ERROR`).
- `message`: A description of the log event.

Log levels must be written in uppercase.

### Example CSV File

```csv
timestamp,level,message
2026-01-03T09:00:00Z,INFO,Startup complete
2026-01-03T09:05:00Z,WARN,Memory usage high
2026-01-03T09:10:00Z,ERROR,Connection lost
```

See the [sample CSV file](data/sample_logs.csv) for the full example.

## Data Privacy

LogLens processes CSV files locally on the user's computer. It does not upload, transmit, or store input data outside the user's computer.

The program reads and counts log records without modifying or repairing the original CSV file. It does not diagnose system failures.

## Troubleshooting and Support

If you have trouble setting up or running LogLens, refer to the [Installation Guide](docs/INSTALL.md).

When reporting an issue on GitHub, describe the problem and provide a small example with any sensitive information removed.

Do not publicly share CSV files containing private or sensitive information.
