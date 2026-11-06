# 使用技巧

## 文件索引

Drive2dav 会在你浏览文件时自动建立索引，如果文件源有变动，你可以点击如下图所示的同步图标刷新并重建索引。

![fs-list-refresh](/images/fs-list-refresh.webp)

## 文件保险箱

对文件加密以保护你的隐私，Drive2dav 会在你阅览/播放时自动解密。

### 加密

```sh
$ drive2dav encrypt <pattern...>
```

### 解密

```sh
$ drive2dav decrypt <pattern...>
```

> [!TIP]
> `pattern` 为要加解密的文件/目录，支持通配符，比如 `drive2dav encrypt "*.mp4"` 表示加密当前目录下的所有 MP4 文件。

> [!IMPORTANT]
> 加密文件的文件名会以 `.d2dcrypt` 结尾，**切勿对文件名做任何修改** ，否则 Drive2dav 将无法正确解密。
