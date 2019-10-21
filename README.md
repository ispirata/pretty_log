# PrettyLog

PrettyLog is an Elixir library which provides some ready-to-use log formatters, including a Logfmt formatter.

## Using PrettyLog

Just change the `:format` config entry in your config/{prod,dev,test}.exs files:

```
-config :logger, :console, format: "[$level] $message\n"
+config :logger, :console,
+  format: {PrettyLog.LogfmtFormatter, :format},
+  metadata: [:module, :request_id, :tag]
```

metadata is arbitrary and optional.

## Formatter Vs Backend

Formatter and logger backend are two distinct components.
- The formatter transforms a log message and its metadata into a binary
- The logger backend outputs log binaries

This library is focused on logs formatting, leaving to you the choice about your favourite backend.
