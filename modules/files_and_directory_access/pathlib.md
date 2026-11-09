´# pathlib

## What is it?

A module for working with files, directories, and file paths.

Think of it as Python's modern way of interacting with the file system.

Instead of building file paths as strings, `pathlib` provides objects that make file and directory operations easier to read, write, and maintain.

---

## When would I use it?

Use `pathlib` when your Python code needs to:

- Read files
- Write files
- Create directories
- Check whether a file exists
- Find files in a directory
- Build file paths safely
- Traverse folder structures

---

## Common problems it solves

- How do I check whether a file exists?
- How do I read a file?
- How do I write a file?
- How do I create a directory?
- How do I find all PDF files in a folder?
- How do I build file paths without worrying about Windows vs Linux path separators?

---

## Real-world examples

You might use `pathlib` to:

- Load a configuration file when your application starts
- Scan a directory for CSV files that need processing
- Generate reports and save them to an output folder
- Find and archive log files
- Build file paths in a cross-platform application
- Create upload and download directories in a web application

The `pathlib` module is commonly used in:

- Data processing scripts
- Backend applications
- CLI tools
- Automation scripts
- ETL pipelines
- Machine learning projects

---

## Example

The most important class in the `pathlib` module is:

```python
Path
```

Think of a `Path` object as:

> "A file or directory that Python can interact with."

---

### Creating a Path Object

```python
from pathlib import Path

file = Path("notes.txt")

print(file)
```

Output:

```text
notes.txt
```

Most operations in `pathlib` start by creating a `Path` object.

---

### Checking Whether a File Exists

One of the most common tasks when working with files is checking whether a file exists.

```python
from pathlib import Path

file = Path("notes.txt")

if file.exists():
    print("File exists")
else:
    print("File does not exist")
```

Use this when:

- Loading configuration files
- Verifying uploaded files
- Checking for generated reports
- Preventing file-not-found errors

---

### Reading a File

You can read a text file with a single method call.

```python
from pathlib import Path

file = Path("notes.txt")

content = file.read_text()

print(content)
```

This is often cleaner than using:

```python
with open(...) as f:
```

for simple use cases.

---

### Writing a File

You can write text to a file just as easily.

```python
from pathlib import Path

file = Path("notes.txt")

file.write_text("Hello from pathlib!")
```

After running the code:

```text
notes.txt
```

will contain:

```text
Hello from pathlib!
```

Use this when:

- Generating reports
- Saving logs
- Writing configuration files
- Exporting results

---

### Creating Directories

Applications often need to create directories before writing files.

```python
from pathlib import Path

output_dir = Path("output")

output_dir.mkdir(exist_ok=True)
```

The argument:

```python
exist_ok=True
```

prevents an error if the directory already exists.

This is commonly used when:

- Creating report directories
- Setting up project folders
- Creating upload/download locations

---

### Building File Paths

One of the biggest advantages of `pathlib` is building paths safely.

```python
from pathlib import Path

project_dir = Path("reports")

report_file = project_dir / "sales.csv"

print(report_file)
```

Output:

```text
reports/sales.csv
```

The `/` operator automatically builds valid paths.

This works correctly on:

- Windows
- Linux
- macOS

Without needing to manually concatenate strings.

---

### Finding Files

You can easily search for files.

```python
from pathlib import Path

pdf_files = Path(".").glob("*.pdf")

for file*in pdf_files:
    print(file)
```

This example finds all PDF-files in the current directory.

Use this when:

- Processing images
- importing CSV data
- Finding log files
- Batch processing documents

---

### Real-World Example

Suppose you're building a script that processes all CSV files in a folder.

```python
from pathlib im*ort Path

*ata_dir = Path("data")

for csv_file in data_dir*glob("*.csv"):
    print(f"Processing: {csv_file}")
```

Example output:

```text
Processing: sales.csv
Processing: customers.csv
Processing: products.csv
```

Here `pathlib` makes it easy to locate all files matching a pattern and process them automatically.

---

## Why Many Developers Prefer pathlib

Before `pathlib`, Python developers often used:

```python
os.path
```

for path operations.

Today, many developers prefer `pathlib` because it:

- Is easier to read
- Produces cleaner code
- Uses objects instead of string manipulation
- Makes path operations more intuitive

For many new projects, `pathlib` is considered the recommended approach.

---

## Key Takeaway

Use `pathlib` whenever your Python code needs to work with files or directories.

It's particularly useful for:

- Reading files
- Writing files
- Creating directories
- Finding files
- Building file paths safely

Think of it as:

> Python's modern toolkit for interacting with the file system.