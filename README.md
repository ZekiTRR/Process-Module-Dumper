[Russian version (Русская версия)](README_RUSSIAN.md)

# Process Module Dumper

A C++ utility for Windows designed to enumerate loaded modules (DLLs) and their base addresses within a process's address space. This tool is useful for reverse engineering, debugging, and software analysis.

## Key Features

*   **Search by Name**: Finds a process by its executable name (e.g., `example.exe`).
*   **PID Extraction**: Automatically determines the Process ID.
*   **Module Enumeration**: Lists all loaded libraries and the main executable.
*   **Base Addresses**: Displays the starting addresses of modules in memory (VA - Virtual Address).
*   **Data Export**: Optional saving of results to a text file named `<process_name>_modules_dump.txt`.

## How It Works

The program utilizes the Windows API (`tlhelp32.h`) and the `CreateToolhelp32Snapshot` function with `TH32CS_SNAPMODULE` and `TH32CS_SNAPMODULE32` flags. This ensures correct data retrieval for both 32-bit and 64-bit modules within the target process.

## Requirements

*   **OS**: Windows (x86/x64).
*   **Compiler**: Any modern C++ compiler with Windows SDK support (Visual Studio MSVC recommended).
*   **Permissions**: Administrator privileges may be required to access system processes or processes running under a different user.

## Usage Instructions

1.  Compile the `base_address.cpp` file.
2.  Run the compiled executable.
3.  Enter the process name (including the `.exe` extension).
4.  Confirm or decline saving the log (press `y` or `n`).

## Example Output

```text
Enter process name (e.g., example.exe): example.exe
[+] Process found. PID: 14520
Save module list and addresses to file? (y/n): y

Module List:
Module Name                         | Base Address
------------------------------------------------------------
example.exe                        | 0x7FF7087A0000
ntdll.dll                         | 0x7FFF70870000
client.dll                        | 0x7FFF092F0000
engine.dll                        | 0x7FFEBE230000

```
