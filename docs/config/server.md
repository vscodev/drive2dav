# 服务器配置

对应配置文件的 `server` 项。

```json
{
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
```
