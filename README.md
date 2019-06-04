Logging library with MDC support
================================

A Golang implementation of a structured logging library with Mapped Diagnostics Context (MDC) support.

Overview
--------

### Initialization

A new logger instance is created with InitLogger function. Process identity is given as a parameter.

### Mapped Diagnostics Context 

The MDCs are key-value pairs, which are included to all log entries by the library.
The MDC pairs are logger instance specific.

### Log entry format 

Each log entry written the library contains

 * Timestamp
 * Logger identity
 * Log entry severity
 * MDC pairs of the logger instance
 * Log message text

Currently the library only supports JSON formatted output written to standard out of the process

*Example log output*

`{"ts":1551183682974,"crit":"INFO","id":"myprog","mdc":{"second key":"other value","mykey":"keyval"},"msg":"hello world!"}`

Example
-------

```go
package main

import (
	mdcloggo "gerrit.o-ran-sc.org/com/golog"
)

func main() {
	logger, _ := mdcloggo.InitLogger("myname")
	logger.MdcAdd("mykey", "keyval")
    logger.Info("Some test logs")
}
```

License
-------
 Copyright (c) 2019 AT&T Intellectual Property.
 Copyright (c) 2018-2019 Nokia.

 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at

     http://www.apache.org/licenses/LICENSE-2.0

 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
