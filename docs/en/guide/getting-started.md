# Getting Started

## Download and install

Drive2dav is written in Go and runs on all major platforms. Just download the binary for your platform from the [Releases](https://github.com/vscodev/drive2dav/releases) page and run it — no extra dependencies needed.

## Start using it

Start the Drive2dav service:

```sh
$ drive2dav serve
```

> [!TIP]
> On Windows you can simply double-click `drive2dav.exe`.

The program listens on port `8307` by default. Once the service is up, open `http://localhost:8307` in your browser. If everything is fine, you will see the page below.

![login](/images/login.webp)

> [!NOTE]
> The program needs to be initialized on its first run.

## Windows service

You can register Drive2dav as a Windows service, so that the console window does not have to stay open, and the service can start automatically on boot.

### Install the service

```sh
$ .\drive2dav.exe service install
```

### Start the service

```sh
$ .\drive2dav.exe service start
```

### Stop the service

```sh
$ .\drive2dav.exe service stop
```

### Uninstall the service

```sh
$ .\drive2dav.exe service uninstall
```

> [!TIP]
> A service no longer prints logs to the console. It is therefore recommended to run Drive2dav in the foreground once to initialize the administrator account before registering it as a service.

## Docker deployment

Create a working directory, for example `drive2dav`.

```sh
$ mkdir drive2dav
$ cd drive2dav
```

Create a `docker-compose.yml` file with the following content:

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

Then run:

```sh
$ docker compose up -d
```

## Reverse proxy

Add the following block to the `server` section of your Nginx site configuration:

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
