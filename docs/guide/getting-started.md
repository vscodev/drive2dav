# 快速开始

## 下载安装

Drive2dav 使用 Go 语言开发，支持跨平台，只需前往 [Releases](https://github.com/vscodev/drive2dav/releases) 页面下载适用于你平台的二进制文件即可执行，无需额外依赖。此外，你还可以使用包管理器：

### [Homebrew](https://brew.sh)

```sh
$ brew install vscodev/tap/drive2dav
```

### [Scoop](https://scoop.sh)

```sh
$ scoop bucket add vscodev https://github.com/vscodev/scoop-bucket.git
$ scoop install vscodev/drive2dav
```

## 开始使用

启动 Drive2dav 服务：

```sh
$ drive2dav serve
```

> [!TIP]
> Windows 系统可直接双击 `drive2dav.exe` 运行。

程序默认监听 `8307` 端口，启动服务后通过浏览器访问 `http://localhost:8307` 即可。如果一切正常，你将会看到如下图所示的页面。

![login](/images/login.webp)

首次运行程序会自动创建管理员帐号，请留意控制台输出的日志。

```
successfully created admin account, the username is [admin] and password is [xxxxxx]
```

> [!TIP]
> 如果你忘记了管理员密码，可运行 `drive2dav admin reset-pwd` 命令重置。

## Windows 服务

你可以将 Drive2dav 注册为 Windows 服务，这样命令行窗口不用常驻，并支持开机自启。

### 注册服务

```sh
$ .\drive2dav.exe service install
```

### 启动服务

```sh
$ .\drive2dav.exe service start
```

### 停止服务

```sh
$ .\drive2dav.exe service stop
```

### 卸载服务

```sh
$ .\drive2dav.exe service uninstall
```

> [!TIP]
> 由于程序作为服务运行后控制台将不再输出日志，建议先前台运行 Drive2dav 一次初始化管理员帐号再将其注册为服务。

## Docker 部署

创建一个工作目录，例如 `drive2dav` 。

```sh
$ mkdir drive2dav
$ cd drive2dav
```

新建 `docker-compose.yml` 文件并填入以下内容：

```yaml
name: drive2dav

services:
  server:
    image: vscodev/drive2dav:latest
    ports:
      - "8307:8307"
    volumes:
      - "./data/:/var/lib/drive2dav/"
    environment:
      - TZ=Asia/Shanghai
      - PUID=0
      - PGID=0
      - UMASK=022
    restart: unless-stopped
```

然后运行：

```sh
$ docker compose up -d
```

## 反向代理

在 Nginx 网站配置文件的 `server` 块中添加

```
location / {
    proxy_pass http://127.0.0.1:8307;
    proxy_http_version 1.1;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Forwarded-Port $server_port;
}
```
