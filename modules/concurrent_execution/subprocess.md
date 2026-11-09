# subprocess

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

```python
import subprocess

result = subprocess.run(
    ["git", "status"],
    capture_output=True,
    text=True
)

print(result.stdout)
```