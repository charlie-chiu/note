# SSL / TLS Certificate

SSL: Secure Sockets Layer (已被更新的 TLS 取代，但習慣上還是用 SSL 稱呼)

TLS: Transport Layer Security Protocol

[Security SSL — HTTPS 背後的功臣 | Starbugs Weekly 星巴哥技術專欄 | Medium](https://medium.com/starbugs/security-ssl-https-%E8%83%8C%E5%BE%8C%E7%9A%84%E5%8A%9F%E8%87%A3-df714e4df77b)

# check certificate with openssl

```bash
openssl s_client -connect {host} -servername {servername}

openssl s_client -connect 34.92.229.26:443 -servername nicecun.com -state

```

# ACME

Automatic Certificate Management Environment

由 Let's Encrypt 實作的協議，用以獲得憑證

## 驗證方式

目的：驗證申請者是否擁有所申請的網域

### HTTP-01 Challenge

如其名，使用 HTTP 80 pot 來確認

```bash
http://<YOUR_DOMAIN>/.well-known/acme-challenge/<TOKEN>
```

無法用以生成 Wildcard 憑證

### DNS-01 Challenge

設定較繁瑣

必須放在網域的 TXT 記錄下，也就是必須有 DNS 的管理權

可以用以生成 Wildcard 憑證