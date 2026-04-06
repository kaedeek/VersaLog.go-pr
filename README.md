# What is VersaLog.go?

[![Go Version](https://img.shields.io/badge/go-%3E%3D1.19-blue.svg)](https://golang.org/)
[![Go Report Card](https://goreportcard.com/badge/github.com/VersaLog/VersaLog.go)](https://goreportcard.com/report/github.com/VersaLog/VersaLog.go)
[![Go Reference](https://pkg.go.dev/badge/github.com/VersaLog/VersaLog.go.svg)](https://pkg.go.dev/github.com/VersaLog/VersaLog.go)
[![Downloads](https://img.shields.io/github/downloads/VersaLog/VersaLog.go/total.svg)](github.com/VersaLog/VersaLog.go/releases)

What is VersaLog.go?
VersaLog is a powerful and flexible logging library for Golang.
It supports everything from simple usage to advanced, highly customizable configurations to meet a wide range of needs.

## Feature

### Basic Logging

- Supports standard log levels:
   - `INFO`, `ERROR`, `WARNING`, `DEBUG`, `CRITICAL`
- Colored output for better readability
- Symbol-based prefixes (e.g. `[+]`, `[-]`, `[!]`)

### Multiple Output Formats

**Easily switch between different log styles:**

- `simple` → `[+] message`
- `simple2` → `[TIME] [+] message`
- `detailed` → `[TIME][LEVEL] : message`
- `file` → `[FILE:LINE][LEVEL] message`

### Tag System

- Add custom tags to logs
- Supports multiple tags (e.g. `["API", "AUTH"]`)
- Optional default tags

### File & Line Tracking

- Display caller file name and line number
- Useful for debugging large projects

### Log File Saving

- Automatically save logs to files
- Output path: `./log/YYYY-MM-DD.log`
- Select which log levels to save

### Auto Cleanup

- Automatically deletes old log files (default: 7 days)
- Keeps your log directory clean

### Auto Cleanup

- Disable console output
- Useful for background services

### Exception Handling

- Automatically captures unhandled exceptions
- Logs them as `CRITICAL`

### Desktop Notifications

- Optional desktop alerts for errors and critical logs
- Uses `plyer.notification`

### Asynchronous Logging

- Non-blocking log processing using threads and queues
- Improves performance in high-load environments

## Support

Join our Discord server for support, questions, and community discussions:

[![Discord](https://img.shields.io/badge/Discord-Support%20Server-7289DA?style=flat&logo=discord)](https://discord.gg/Ms2ejEES)

## Installation

```
go get github.com/VersaLog/VersaLog.go
```

### Enum

| Enum       | Description                                                                  |
| ---------- | ---------------------------------------------------------------------------- |
| `detailed` | Logs including execution time and log levels                                 |
| `file`     | Logs with filename and line number                                           |
| `simple`   | Simple and easy-to-read logs                                                 |
| `simple2`  | Simple and easy-to-read log format. The timestamp is automatically included. |

### Options

| Options            | Description                                                                                                                                                                     |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `show_file`        | True : Display filename and line number (for simple and detailed modes)                                                                                                         |
| `show_tag`         | True : Show self.tag if no explicit tag is provided                                                                                                                             |
| `tag`              | Default tag to use when show_tag is enabled                                                                                                                                     |
| `enable_all`       | Shortcut to enable both show_file and show_tag                                                                                                                                  |
| `notice`           | True : When an error or critical level log is output, a desktop notification (using plyer.notification) will be displayed. The notification includes the log level and message. |
| `all_save`         | True : When an error or critical level log is output, the log will be saved to a file.                                                                                          |
| `save_levels`      | A list of log levels to save. Defaults to ["INFO", "ERROR", "WARNING", "DEBUG", "CRITICAL"].                                                                                    |
| `silent`           | True : Suppress standard output (print)                                                                                                                                         |
| `catch_exceptions` | True : Automatically catch unhandled exceptions and log them as critical                                                                                                        |

## Tag set(two tag)

```

logger := versalog.NewVersaLog(
    "detailed",        // enum
    false,             // showFile
    true,              // showTag
    "VersaLog,Core",   // tag(Two items separated by a comma)
    false,             // enableAll
    false,             // notice
    false,             // allSave
    []string{},        // saveLevels
    false,             // silent
    false,             // catchExceptions
)
```

## Log save

```
[2025-08-06 04:10:36][INFO] : ok
```