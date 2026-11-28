# Server

Corresponds to the `server` section of the configuration file.

| Field                  | Type     | Default    | Description                                                                                 |
|------------------------|----------|------------|---------------------------------------------------------------------------------------------|
| `host`                 | string   | `0.0.0.0`  | Listen address. `0.0.0.0` allows access from the LAN or outside, `127.0.0.1` allows local access only. |
| `port`                 | number   | `8307`     | Listen port.                                                                                |
| `tls.enabled`          | bool     | `false`    | Whether to enable HTTPS.                                                                    |
| `tls.cert_file`        | string   | `""`       | Path of the certificate file (PEM). Required when TLS is enabled.                            |
| `tls.key_file`         | string   | `""`       | Path of the private key file (PEM). Required when TLS is enabled.                            |
| `cors.enabled`         | bool     | `true`     | Whether to enable cross-origin support.                                                      |
| `cors.allowed_origins` | string[] | `["*"]`    | List of origins allowed to make cross-origin requests, e.g. `["https://example.com"]`. `*` allows all origins. |
| `ip_extractor`         | string   | `"direct"` | How the real client IP is obtained, see the table below.                                     |
| `trusted_proxies`      | string[] | `[]`       | List of trusted proxies (CIDR or IP). Only effective when `ip_extractor` is `xff` or `real_ip`. |

Values of `ip_extractor`:

| Value     | Description                                                                                          |
|-----------|------------------------------------------------------------------------------------------------------|
| `direct`  | Use the source IP of the TCP connection directly. For direct deployments without a reverse proxy.     |
| `xff`     | Resolve the real IP from the `X-Forwarded-For` header. Use it behind Nginx, Cloudflare and similar reverse proxies. |
| `real_ip` | Resolve the real IP from the `X-Real-IP` header. Suitable for Nginx's default forwarding configuration. |
