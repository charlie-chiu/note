# 2020 gode 部署

遇到有趣的問題：第一次 DNS resolve 會很久

[https://github.com/golang/go/issues/21906](https://github.com/golang/go/issues/21906)

[https://github.com/golang/go/issues/26960](https://github.com/golang/go/issues/26960)

[linux - Difference between /etc/hosts and /etc/resolv.conf - Server Fault](https://serverfault.com/questions/118923/difference-between-etc-hosts-and-etc-resolv-conf)

[https://github.com/golang/go/issues/22846](https://github.com/golang/go/issues/22846)

echo "hosts: files dns" > /etc/nsswitch.conf
