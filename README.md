# pine
<p align="center">
    🌲 A completely useless (but cute) logger for Golang ✨
</p>
<p align="center">
<a href="https://godoc.org/github.com/heyvito/pine"><img src="https://godoc.org/github.com/heyvito/pine?status.svg" alt="GoDoc"></a>
<img src="https://github.com/heyvito/pine/workflows/Build/badge.svg" />
<a href="https://goreportcard.com/report/github.com/heyvito/pine"><img src="https://goreportcard.com/badge/github.com/heyvito/pine" /></a>
</p>

**Pine** is a completely useless (but cute) logger for Golang. Its output may not be ideal to parse,
but at least there's Emojis and color. 🙌

<p align="center">
<img src="https://i.imgur.com/4D9ATE7.png" />
</p>

## Installing
1. Download and install it

```bash
$ go get -u github.com/heyvito/pine
```

2. Import it in your code:

```go
import "github.com/heyvito/pine"
```

## Usage
Pine exports a `NewWriter` method that creates a new logger instance with a given
module name. The logger instance has a few methods that prints data with an associated
emoji. The following methods (and their emojis) are available:

|  Method   | Emoji |
|-----------|-------|
| Bug       |  🐞  |
| Disk      |  📀  |
| Error     |  🛑  |
| Finish    |  🆗  |
| Info      |  💬  |
| Lock      |  🔒  |
| Plug      |  🔌  |
| Secure    |  🔑  |
| Sleep     |  💤  |
| Spawn     |  ✨  |
| Success   |  🟢  |
| Terminate |  ⭕  |
| Thread    |  🧵  |
| Timing    |  ⏱  |
| Warn      |  🟡  |
| WTF       |  👻  |

For instance, the following snippet:

```go
logger := pine.NewWriter("ModuleName")
logger.WTF("What is going %s?", "on")
logger.Success("Even more logging!")
```
Yields the following log line:

```
18:27:38 👻  ModuleName What is going on?
18:27:38 🟢  ModuleName Even more logging!
```

Every logging method has an extra method that prefixes a message with extra data:

```go
logger.PlugExtra("Extra Data!", "A cute formatted %s", "message")
```

Yielding the following line:

```
18:27:38 🔌  ModuleName Extra Data! A cute formatted message
```

As you may think, it is quite boring to repetitively include the `extra` parameter
and keep calling `PlugWithExtra` all the time. For those cases, you can call `WithExtra`,
that attaches the provided data to the next log calls. For instance, take the following snippet:

```go
extraLogger := logger.WithExtra("Attached data")
extraLogger.Plug("Another sweet %s", "message")
extraLogger.Finish("Process completed.")
```

Yielding, then, the following result:

```
18:27:38 🔌  ModuleName Attached data Another sweet message
18:18:38 🆗  ModuleName Attached data Process completed.
```

## License
```
MIT License

Copyright (c) 2017 Victor Gama

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
