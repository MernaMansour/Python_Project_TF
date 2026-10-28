# Python File Management Utility

A Python learning project that implements common file and directory operations in two styles: an interactive, menu-driven program and a command-line interface built with `argparse`.

## Overview

This repository contains two Jupyter notebooks that demonstrate file-system automation using Python's standard library. Both versions are designed around a `File_handling` class and cover searching for a file, renaming it, replacing text in a file, copying files, moving files, and locating a filename within a directory tree.

## Features

| Operation | Description | Python module/function |
| --- | --- | --- |
| Search | Check whether a specified file or path exists | `os.path.exists` |
| Rename | Rename a file or path | `os.rename` |
| Modify | Replace matching text in an existing text file | `open`, `str.replace` |
| Copy | Copy one or more files between directories | `shutil.copyfile` |
| Move | Move one or more files between directories | `shutil.move` |
| Find | Walk through subdirectories to locate a filename | `os.walk` |

## Repository Files

```text
.
├── Python Project without arg parser.ipynb
├── project_with_parser.ipynb
└── README.md
```

### 1. Interactive version

**`Python Project without arg parser.ipynb`** uses `input()` to ask the user which operation to perform. Its menu uses these letters:

| Input | Operation |
| --- | --- |
| `S` | Search |
| `R` | Rename |
| `M` | Modify file contents |
| `C` | Copy files |
| `X` | Move files |
| `F` | Find a file's directory |

### 2. Command-line version

**`project_with_parser.ipynb`** defines `argparse` subcommands (`search`, `rename`, `modify`, `copy`, `move`, and `find`) and their arguments. This version illustrates how the same operations can be requested from the terminal rather than through a sequence of interactive prompts.

## Requirements

- Python 3
- Jupyter Notebook or JupyterLab to open and run the `.ipynb` files

The file-operation logic uses Python's standard-library modules `os` and `shutil`. The command-line version additionally uses `argparse` (also part of the standard library); no third-party package is needed for these functions.

## Getting Started

1. Download or clone the repository.
2. Open the desired notebook in Jupyter Notebook, JupyterLab, or VS Code with the Jupyter extension.
3. Review the **Known Issues** section below before executing file-changing operations.
4. Run the cells and supply paths to test files that you are comfortable modifying.

> **Safety:** Rename, modify, move, and copy operations affect actual files. Test with disposable files first, and keep backups of important data.

## Known Issues and Improvements

These notebooks demonstrate the intended operations, but the uploaded versions contain issues that need to be corrected before all menu and command-line actions will run reliably:

- In both versions, the functions inside `File_handling` are defined without a `self` parameter. Call them on the class as in the interactive notebook, add `@staticmethod`, or convert them into normal instance methods with `self`.
- In `project_with_parser.ipynb`, add `import argparse` before creating the parser.
- In the parser-based notebook, `find_file_directory` is currently indented inside `Move_file`, whereas the dispatcher calls `Find_file_directory`. Move it to the class level and make its name match the call.
- The parser version currently creates `File_handling()` and calls methods on that instance; this conflicts with the methods that do not accept `self`.
- Consider checking source file existence, destination directory existence, and file permissions, and handling exceptions before modifying the filesystem.
- `Modify_content` replaces *every* occurrence of the specified text and overwrites the file. It is intended for text files, not binary formats.

## Learning Objectives

- Work with files and directory paths in Python.
- Use `os` and `shutil` for common file operations.
- Build a simple menu-driven application with `input()`.
- Understand command-line arguments and subcommands with `argparse`.
- Organize reusable functionality in classes.

## Future Enhancements

- Fix the method definitions and parser-based `find` command.
- Add clear success and error messages for each operation.
- Validate inputs and handle missing files or directories.
- Add unit tests and a safer dry-run option.
- Optionally export the tested notebook logic into runnable `.py` scripts.

## Project Status

**Educational prototype.** The notebooks illustrate the design of two interfaces for the same file-management operations; fixes listed above are needed for reliable execution.
