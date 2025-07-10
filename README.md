# MicroPython Development Toolkit

*[中文版 README](README.zh.md)*

A collection of tools for MicroPython development, providing file upload, device monitoring, and hot reload functionality.

## Quick Start

1. Install dependencies:
    ```shell
    pip install -r requirements.txt
    ```
2. configure .env of serial info
    ```shell
    echo "DEVICE=/dev/ttyUSB0" >> .env
    echo "BAUD=115200" >> .env
    ```
3. 
    ```shell
    # Initial upload of all files
    python upload.py --all
    # start serial monitor
    python monitor.py
   
    # or all in one
    # Use hot reload during development
    python reload.py
    ```
## Tools Overview

### 1. upload.py - File Upload Tool
Upload tool for synchronizing local Python files to MicroPython devices. (Automatically restarts)

**Usage:**
```
bash
# Upload modified files
python upload.py

# Force sync all files (clears device first, then uploads)
python upload.py --all
```
### 2. monitor.py - Serial Monitor Tool
Real-time monitoring of MicroPython device serial output, useful for debugging and viewing program execution status. Supports command interaction, auto-reconnect, and RAW REPL mode.

**Usage:**
```bash
# Basic usage
python monitor.py

# Disable timestamp display
python monitor.py --no-timestamps

# Disable auto-reconnect
python monitor.py --no-reconnect

# Start in RAW REPL mode
python monitor.py --raw-repl
```
```


**Built-in Commands:**
```
help        - Show help information
stats       - Show connection statistics
reconnect   - Reconnect to device
raw         - Toggle RAW REPL mode
reset       - Send soft reset (Ctrl+D)
exit/quit   - Exit monitor

# Use Ctrl+C to exit
```


### 3. reload.py - Hot Reload Tool
Combined tool that automatically uploads changed files and starts monitoring. (Automatically restarts)

**Usage:**
```shell script
python reload.py
```


## Environment Configuration

Create a `.env` file and configure the following parameters:

```
DEVICE=/dev/ttyUSBx (on Win: COMx)    # Device path
BAUD=115200                           # Baud rate
```


## Directory Structure

```
.
├── src/             # pyboard source code directory
├── .uploaded/       # Upload file hash cache
├── .env             # Environment variable configuration
├── upload.py        # File upload tool
├── monitor.py       # Serial monitor tool
└── reload.py        # Hot reload tool
```