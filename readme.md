# prodonik_lgger

A lightweight, structured logging wrapper for [Logrus](https://github.com/sirupsen/logrus), providing JSON-formatted logs and simplified global logger usage for Go applications.

## Features

- JSON formatted logs with timestamps.
- Configurable output to a file.
- Log levels: `Debug`, `Info`, `Warn`, `Error`.
- Optional support for structured fields (key-value pairs).
- Easy to use globally across multiple services or microservices.

## Installation

To use `prodonik_lgger` in your Go project, you can import it directly from GitHub:

```go
import logger "github.com/ruziba3vich/prodonik_lgger/logger"
```
Make sure to run:
```shell
go get github.com/ruziba3vich/prodonik_lgger/logger
```

## Usage

Here's how to set up and use the logger globally in your project:

### 1. Initialize the Logger

```go

package main

import (
    logger "github.com/ruziba3vich/prodonik_lgger/logger"
)

var log *logger.Logger

func init() {
    var err error
    log, err = logger.NewLogger("app.log")
    if err != nil {
        panic(err)
    }
}
```

### 2. Use the Logger in Your Code

```go
func main() {
    log.Info("Application started")

    log.Debug("Debugging something", map[string]any{
        "module": "main",
        "step":   1,
    })

    log.Warn("This is a warning")

    log.Error("An error occurred", map[string]any{
        "error_code": 123,
    })
}
```

## Methods

```
Method | Description
Debug(msg, fields...) | Logs a debug message (if fields provided, logs them too).
Info(msg, fields...) | Logs an info message.
Warn(msg, fields...) | Logs a warning message.
Error(msg, fields...) | Logs an error message.

`fields` is an optional parameter of type map[string]any that adds extra structured data to your logs.
```

## Example Output

```json
{
  "level": "info",
  "msg": "Application started",
  "time": "2025-04-25T12:00:00Z"
}
```

With fields:

```json
{
  "level": "debug",
  "msg": "Debugging something",
  "module": "main",
  "step": 1,
  "time": "2025-04-25T12:01:00Z"
}
```

## 💡 Contributing

-- Feel free to fork and contribute! PRs are welcome.
