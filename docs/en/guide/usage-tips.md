# Usage Tips

## File index

Drive2dav indexes your files automatically while you browse them. If the file source has changed, click the sync icon shown below to refresh and rebuild the index.

![fs-list-refresh](/images/fs-list-refresh.webp)

## File Vault

Encrypt your files to protect your privacy; Drive2dav decrypts them automatically when you view or play them.

### Encrypt

```sh
$ drive2dav encrypt <pattern...>
```

### Decrypt

```sh
$ drive2dav decrypt <pattern...>
```

> [!TIP]
> `pattern` is the file or directory to encrypt or decrypt and supports wildcards. For example, `drive2dav encrypt "*.mp4"` encrypts every MP4 file in the current directory.

> [!IMPORTANT]
> Encrypted files get the `.d2dcrypt` suffix in their names. **Never modify these file names**, otherwise Drive2dav will not be able to decrypt them correctly.
