# WWT Logger
The logger module was created in order to log specific information. The template looks like this:
>**Example**: 
>&nbsp;&nbsp;&nbsp;ERROR [Thu, 19 Nov 2020 19:14:58 GMT]: Something went wrong with the database connection

### Installation :
>npm install **@addesign/wwt-logger**
NPM: https://www.npmjs.com/package/@addesign/wwt-logger

#### An example of using the logger: 
```
const path = require("path");
const Logger = require("@addesign/wwt-logger)

const logger_instance = new Logger({ dir: path.join(__dirname, "logs") });
const {logType} = logger_instance
```
In order to add an entry to the log file, use the following code:
```
logger_instance.set(logeType.ERROR, `something text for log file`, (err) => { callback })
```
To get the file, just use the get method and we can use the built-in types: 
```
const {logType} = logger_instance
logger_instance.get(logType.ERROR, (err, data) => { callback })
```

#### An example of using a logger to write all logs to one file:
```
const path = require("path");
const Logger = require("@addesign/wwt-logger")
const loggerConfig = { 
    dir: path.join(__dirname, "your directory"),
    singleFile: true, 
    singleFileName: "logsFileExample"
}

const instanceLogger = new Logger(loggerConfig)
```
If **singleFile** is specified, then **singleFileName** must be specified.
The **singleFileName** property in the LoggerConfig must not contain **".log"** at the end of the file name.
#### An example of using the logger with Express.js: 

```
const path = require("path");
const ExpressLogger = require("@addesign/wwt-logger/express")
...
const loggerConfig = { dir: path.join(__dirname, "your directory") }

app
  .use(ExpressLogger(loggerConfig))
  .use((req) => {
    req.logger.logType // log types
    req.logger.get(...)
    req.logger.set(...)
  });
```

**All logger types:**
```
enum LogTypes {
  ERROR = "ERROR",
  INFO = "INFO",
  WARNING = "WARNING",
  DEBUG = "DEBUG",
  FATAL = "FATAL"
}
```

# Licence

**Copyright (c) 2020 AD design ©**

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

**THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.**
