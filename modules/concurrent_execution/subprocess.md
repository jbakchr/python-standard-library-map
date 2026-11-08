# subprocess

## What is it?

A module for running external programs and shell commands from Python.

## When would I use it?

Use subprocess when Python needs to:

- Run git commands
- Run Docker commands
- Execute shell scripts
- Launch another program
- Capture command output

## Common problems it solves

- How do I run a command from Python?
- How do I automate Git?
- How do I call FFmpeg?
- How do I execute a bash script?

## Example

```python
import subprocess

result = subprocess.run(
    ["git", "status"],
    capture_output=True,
    text=True
)

print(result.stdout)´