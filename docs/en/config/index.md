# Configuration File

The configuration file of Drive2dav is always `config.json` in the data directory:

```
<data directory>/config.json
```

### How the data directory is determined

| Scenario                 | Data directory                             |
|--------------------------|--------------------------------------------|
| Official Docker image    | `/var/lib/drive2dav`                       |
| Defaults on other platforms | `drive2dav` in the user configuration directory |

Default locations on each system:

- Linux: `$XDG_CONFIG_HOME/drive2dav`, or `~/.config/drive2dav` when it is not set
- macOS: `~/Library/Application Support/drive2dav`
- Windows: `%AppData%\drive2dav`
