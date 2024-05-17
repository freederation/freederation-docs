# FREEDERATION

This is the whitepaper and documentation that specifies the **FREEDERATION** protocol, a DAO community platform that provides economic support to Open Source projects (Free Software and Public Domain Intellectual Works).



## Requirements

Building the book requires a custom fork of [mdBook]:

[mdBook]: https://github.com/RustLangES/mdBook/

```bash
$ cargo install mdbook --git https://github.com/freederation/freederation-docs.git
```

## Building

To build the book, type:

```bash
$ mdbook build
```

The output will be in the `book` subdirectory. To check it out, open it in
your web browser.

_Firefox:_
```bash
$ firefox book/index.html                       # Linux
$ open -a "Firefox" book/index.html             # OS X
$ Start-Process "firefox.exe" .\book\index.html # Windows (PowerShell)
$ start firefox.exe .\book\index.html           # Windows (Cmd)
```

_Chrome:_
```bash
$ google-chrome book/index.html                 # Linux
$ open -a "Google Chrome" book/index.html       # OS X
$ Start-Process "chrome.exe" .\book\index.html  # Windows (PowerShell)
$ start chrome.exe .\book\index.html            # Windows (Cmd)
```

To run the tests:

```bash
$ mdbook test
```