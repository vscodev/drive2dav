# 配置文件

Drive2dav 的配置文件固定为数据目录下的 `config.json`：

```
<数据目录>/config.json
```

### 数据目录如何确定

| 场景             | 数据目录                         |
|------------------|----------------------------------|
| 官方 Docker 镜像 | `/var/lib/drive2dav`             |
| 其他平台默认值   | 系统用户配置目录下的 `drive2dav` |

各系统的默认位置：

- Linux：`$XDG_CONFIG_HOME/drive2dav`，未设置时为 `~/.config/drive2dav`
- macOS：`~/Library/Application Support/drive2dav`
- Windows：`%AppData%\drive2dav`