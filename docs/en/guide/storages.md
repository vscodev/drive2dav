# Adding Storages

Add and mount a storage as described below. Once mounted, you can connect to it [via WebDAV](/en/guide/webdav).

![mount](/images/mount.webp)

> [!TIP]
> The name of the mounted root folder is the unique identifier of the storage. It corresponds to a top-level folder under the root directory `/`.

## Common options

### Refresh interval

With this option, the program refreshes and rebuilds the file index whenever it retrieves the file list. Set a smaller value if the file source changes frequently, and a larger value if it does not. `0` disables automatic refreshing.

### Force proxy

For cloud drive storages, Drive2dav by default accesses file resources through a redirect when the upstream supports it, which consumes no server bandwidth.

Some cloud drives, however, do not support cross-origin access or return an incorrect MIME type, which prevents the browser from viewing or playing the files. In that case you can turn on **Force proxy** to route the requests through the server.

## Local storage

### Root folder path

The absolute path of the target folder, e.g. `/root`.

## Baidu Netdisk

### Root folder path

An absolute path starting with `/`. The root directory is `/`.

## OneDrive

### Root folder path

An absolute path starting with `/`. The root directory is `/`.

## Google Drive

### Root folder ID

The unique identifier of the folder, which you can copy from the browser address bar.

For the target folder at `https://drive.google.com/drive/folders/1Qd9RC5Lr0J7VHUssBSv5sKDhxnla_GSs`, the trailing string
`1Qd9RC5Lr0J7VHUssBSv5sKDhxnla_GSs` is the folder ID. The root directory is `root`.

## Alibaba Cloud Drive

### Root folder ID

The unique identifier of the folder, which you can copy from the browser address bar.

Take the backup drive as an example: for the target folder at `https://www.alipan.com/drive/file/all/backup/623fbf465be853af1a0f44eb8842bdf76d477da9`,
the trailing string `623fbf465be853af1a0f44eb8842bdf76d477da9` is the folder ID. The root directory is `root`.

## 115 Drive

### Root folder ID

The unique identifier of the folder, which you can copy from the browser address bar.

For the target folder at `https://115.com/?cid=3105489445714151206&offset=0&tab=&mode=wangpan`, the value of the `cid`
query parameter — `3105489445714151206` — is the folder ID. The root directory is `0`.

## 123 Cloud Drive

### Root folder ID

The unique identifier of the folder, which you can copy from the browser address bar.

For the target folder at `https://www.123pan.com/?homeFilePath=15374274,15374275`, the last comma-separated number in the value of
the `homeFilePath` query parameter — `15374275` — is the folder ID. The root directory is `0`.

## Dropbox

### Root folder path

An absolute path starting with `/`. The root directory is `/`.

## Box

### Root folder ID

The unique identifier of the folder, which you can copy from the browser address bar.

For the target folder at `https://app.box.com/folder/309858234060`, the trailing string `309858234060` is the folder ID. The
root directory is `0`.

## Yandex Disk

### Root folder path

An absolute path starting with `/`. The root directory is `/`.

## pCloud

### Root folder ID

The unique identifier of the folder, which you can copy from the browser address bar.

For the target folder at `https://my.pcloud.com/#page=filemanager&folder=25622191431`, the value of the `folder` query parameter —
`25622191431` — is the folder ID. The root directory is `0`.

## WebDAV

### Server address

If you want to add a specific folder instead of the root directory, append the corresponding path to the server address. For
example, if the upstream WebDAV server address is `https://dav.jianguoyun.com/dav/` and the target folder is `/Movies`, enter
`https://dav.jianguoyun.com/dav/Movies` as the server address.
