> WARNING: 基於一特定組織的安裝環境記錄

啟動 command (copy from ns1@leacloud)
```
# 啟動
/usr/sbin/named -u named -4 -t /chroot/named -c /etc/named.conf

# reload ... 或其他指令
/chroot/named/etc/named.sh reload

```

# zonefiles path

`/chroot/named/etc/Global/.../chroot/named/etc/CN/...`

# logs path
`/chroot/named/var/*.log`

# Errors
## CNAME and other data

## _ underscore in record name
A, MX 不可用

## _ underscore in record data
- A 報錯
- NS 報錯
- CNAME