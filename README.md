```md
# FileSplitter Module

## Overview
The FileSplitter module provides PowerShell commands to split a file into multiple parts and to join those parts to recreate the original file. It is useful for handling large files by breaking them into smaller, manageable chunks.

## Features
- **Split-File**: Splits a file into smaller parts with a specified maximum size.
- **Join-File**: Recreates the original file by joining the parts created by `Split-File`.
- **Self-Extractor**: Optionally adds a self-extracting script to simplify the process of joining parts.

## Commands

### Split-File
Splits a file into smaller parts.

#### Syntax
```powershell
Split-File -Path <String> -PartSizeBytes <Int> [-AddSelfExtractor] [-Verbose]
```

#### Parameters
- `-Path`: Path to the file you want to split.
- `-PartSizeBytes`: Maximum size of each part in bytes (default: 1MB).
- `-AddSelfExtractor`: Adds a self-extracting script and shortcut for easy reassembly.
- `-Verbose`: Displays detailed output during execution.

#### Examples
```powershell
# Split a file into parts of 2.5MB each
Split-File -Path 'C:\test.zip' -PartSizeBytes 2.5MB

# Split a file and add a self-extractor
Split-File -Path 'C:\test.zip' -PartSizeBytes 2.5MB -AddSelfExtractor
```

### Join-File
Joins the parts created by `Split-File` to recreate the original file.

#### Syntax
```powershell
Join-File -Path <String> [-DeletePartFiles] [-Verbose]
```

#### Parameters
- `-Path`: Path of the original file (excluding part number and `.part` extension).
- `-DeletePartFiles`: Deletes part files after reassembly.
- `-Verbose`: Displays detailed output during execution.

#### Examples
```powershell
# Join parts to recreate the original file
Join-File -Path 'C:\test.zip'

# Join parts and delete the part files after reassembly
Join-File -Path 'C:\test.zip' -DeletePartFiles
```

## Installation
1. Download the module files.
2. Place them in a directory named `FileSplitter` under one of the paths listed in `$env:PSModulePath`.
3. Import the module using:
    ```powershell
    Import-Module FileSplitter
    ```

## License
(c) 2019 Tobias. All rights reserved.
```md
## Using the Module Locally

If you prefer to use the module without installing it via `Import-Module`, you can run the source code directly. This is useful for testing or development purposes.

### Steps to Use Locally
1. Navigate to the directory containing the module's source files:
    ```powershell
    cd C:\Users\User\Desktop\FileSplitterByISESteroidsPowershellgallery\src
    ```

2. Dot-source the `loader.psm1` file to load the module's functions into your current session:
    ```powershell
    . .\loader.psm1
    ```

3. Use the commands `Split-File` and `Join-File` as needed:
    ```powershell
    # Example: Split a file into parts
    Split-File -Path 'C:\test.zip' -PartSizeBytes 2.5MB

    # Example: Join parts to recreate the original file
    Join-File -Path 'C:\test.zip'
    ```
```
