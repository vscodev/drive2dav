# Logging

Corresponds to the `log` section of the configuration file.

| Field         | Type   | Default                          | Description                                                                                   |
|---------------|--------|----------------------------------|-----------------------------------------------------------------------------------------------|
| `enabled`     | bool   | `true`                           | Whether to write log files. When disabled, logs go to stderr only, and are dropped entirely in Windows service mode. |
| `filename`    | string | `<data directory>/logs/drive2dav.log` | Path of the log file. The directory is created automatically if it does not exist.       |
| `max_size`    | int    | `50`                             | Maximum size of a single log file, **in MB**. The file is rotated once it is exceeded.         |
| `max_backups` | int    | `30`                             | Maximum number of historical log files to keep. `0` means no limit.                            |
| `max_age`     | int    | `28`                             | Number of days to keep historical logs, **in days**. `0` means no time-based cleanup.          |
| `compress`    | bool   | `true`                           | Whether to gzip the rotated historical logs.                                                   |
