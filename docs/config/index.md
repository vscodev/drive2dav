# 配置文件

Drive2dav 的数据目录包含程序配置、应用数据、授权许可证以及日志等内容，根据你使用的平台和安装方式，位置可能有所不同。

| 平台    | 路径                                                      |
|---------|-----------------------------------------------------------|
| Windows | `%AppData%/drive2dav`                                     |
| macOS   | `$HOME/Library/Application Support/drive2dav`             |
| Linux   | `$XDG_CONFIG_HOME/drive2dav` 或 `$HOME/.config/drive2dav` |
| Docker  | `/var/lib/drive2dav`                                      |

数据目录下的 `config.json` 为Drive2dav的运行配置文件，示例：

::: code-group

```json [config.json]
{
  "log": {
    "enabled": true,
    "filename": "$HOME/Library/Application Support/drive2dav/logs/drive2dav.log",
    "max_size": 50,
    "max_backups": 30,
    "max_age": 28,
    "compress": true
  },
  "database": {
    "driver": "sqlite3",
    "data_source": "file:$HOME/Library/Application Support/drive2dav/drive2dav.db?cache=shared&mode=rwc&_busy_timeout=500&_txlock=immediate&_journal_mode=WAL&_foreign_keys=true"
  },
  "server": {
    "tls": {
      "enabled": false,
      "cert_file": "",
      "key_file": ""
    },
    "ip_extractor": {
      "mode": "",
      "trusted_proxies": null
    },
    "bind_host": "0.0.0.0",
    "bind_port": 8307,
    "allow_origins": [
      "*"
    ],
    "allow_methods": [
      "*"
    ],
    "allow_headers": [
      "*"
    ],
    "jwt_secret": "xxxxxx",
    "token_expires_in": 7
  }
}
```

:::

> [!NOTE]
> 配置文件的绝大部分内容都不需要修改，除非你明确知道自己在做什么。修改后需要重启程序才会生效。
