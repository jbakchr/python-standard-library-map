´# subprocess

## What is it?

A module that allows your Python code to execute external programs and shell commands.

Think of it as a bridge between your Python code and programs installed on your computer.

## When would I use it?

Use `subprocess` when your Python code needs to:

- Run Git commands from within a Python script
- Run Docker commands from within a Python application
- Execute Bash or PowerShell scripts
- Launch another program
- Capture and process the output of a command
- Automate command-line tools

## Common problems it solves

- How do I run a shell command from Python?
- How do I automate Git operations?
- How do I execute a Bash script from Python?
- How do I call FFmpeg from Python?
- How do I run Docker commands from my own application?
- How do I get the output of a terminal command?

## Real-world examples

You might use `subprocess` to:

- Build a tool that automatically commits and pushes changes with Git
- Create a Python application that starts Docker containers
- Run FFmpeg to convert video files
- Execute a backup script every night
- Call system utilities and process their results

## Example

The main function you'll use from the `subprocess` module is:

```python
subprocess.run(...)
```

Think of `subprocess.run()` as:

> "Run another program from within my Python code."

---

### Running a Command

The first argument is typically a list containing the command and its arguments.

```python
import subprocess

subprocess.run(["git", "status"])
```

This is equivalent to running:

```bash
git status
```

in your terminal.

The command is provided as a list:

```python
["git", "status"]
```

where:

- `"git"` is the program to run
- `"status"` is an argument passed to that program

You can provide as many arguments as needed:

```python
subprocess.run(
    ["docker", "run", "nginx"]
)
```

which is equivalent to:

```bash
docker run nginx
```

---

### Capturing Command Output

By default, command output is printed directly to the terminal.

If you want your Python code to access the output, use:

```python
capture_output=True
```

Example:

```python
import subprocess

result = subprocess.run(
    ["git", "status"],
    capture_output=True,
    text=True
)

print(result.stdout)
```

Output:

```text
On branch main
nothing to commit, working tree clean
```

Use this when:

- Reading the output of Git commands
- Processing command results in code
- Calling external tools and using their output

---

### Why `text=True`?

Without:

```python
text=True
```

the output is returned as bytes:

```python
b'On branch main\n'
```

With:

```python
text=True
```

the output is returned as a normal Python string:

```python
'On branch main'
```

This makes the result much easier to work with.

```python
result = subprocess.run(
    ["git", "status"],
    capture_output=True,
    text=True
)

print(type(result.stdout))
```

Output:

```python
<class 'str'>
```

For most applications you'll almost always want:

```python
text=True
```

when capturing output.

---

### Failing When a Command Fails

In automation scripts it's often desirable to stop execution if a command fails.

Use:

```python
check=True
```

Example:

```python
import subprocess

subprocess.run(
    ["git", "push"],
    check=True
)
```

If the command fails, Python raises an exception:

```python
subprocess.CalledProcessError
```

This is useful when:

- Deploying applications
- Running backup scripts
- Automating Git workflows
- Executing build pipelines

You generally want your script to fail immediately when an important command fails.

---

### Capturing Errors

You can also access error output.

```python
import subprocess

result = subprocess.run(
    ["git", "push"],
    capture_output=True,
    text=True
)

print(result.stderr)
```

`stderr` contains error messages produced by the command.

This can help with:

- Logging
- Troubleshooting
- Showing useful error messages to users

---

### Real-World Example

Suppose you're creating a Python tool that checks whether a Git repository has uncommitted changes.

```python
import subprocess

result = subprocess.run(
    ["git", "status", "--porcelain"],
    capture_output=True,
    text=True
)

if result.stdout:
    print("Repository contains changes")
else:
    print("Working tree is clean")
```

Here Python is using Git as a subprocess and making decisions based on the command output.

This is one of the most common uses of the `subprocess` module.

---

### Key Takeaway

Use `subprocess` whenever your Python code needs to:

- Execute another program
- Run terminal commands
- Automate command-line tools
- Capture command output
- React to command success or failure

Think of it as Python's way of saying:

> "Run this command for me and let me use the result."