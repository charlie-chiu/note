# Record Name
可包含：字母、數字、 `hyphen - (不能在頭尾)`、 `dot .`

特例：可以為 `@`

特例 `*`：
Type = A, AAAA, CNAME, MX, TXT 時，可以使用`*`
但 CNAME 不可跟其他 record name 同時為 `*`

特例 `@`：
Type = A, AAAA, CNAME, NS, MX, TXT 時，可以使用`@`
但 CNAME 不可跟其他 record name 同時為 `@` (跟 `*` 同原因)
因為 zonefile 一定存在 @ NS ，故 CNAME 不可以為 `@`

特例 `底線 _`：
Type =  CNAME, NS, TXT 時，可以包含`_`


# Record Data
A, AAAA : IPv4, IPv6
TXT:  什麼都可以
CNAME, MX, NS :
可包含：字母、數字、 `hyphen - (不能在頭尾)`、 `dot .`
上限：253 個字
特例：type = CNAME 時，可以為 `@` 、可以包含 `底線 _`


[Link CName record to another domain, but without subdomain - Server Fault](https://serverfault.com/questions/288820/link-cname-record-to-another-domain-but-without-subdomain)
[Is Root domain CNAME to other domain allowed by DNS RFC? - Stack Overflow](https://stackoverflow.com/questions/655235/is-root-domain-cname-to-other-domain-allowed-by-dns-rfc)
