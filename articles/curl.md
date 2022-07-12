# Usage
```bash
#curl with time using -w
curl -I example.com -w %{time_connect}-%"{time_starttransfer}-%{time_total}\n"

#curl without progress bar (using with watch)
curl -s

# with other method
curl -X POST example.com

# with header
curl -H "Host: cache.99x.online" http://182.150.0.18 --verbose

# --verbose or -v to see request header
curl -H "Host: cache.99x.online" http://182.150.0.18 -v

# -k means --insecure, ignore ssl check
curl -k http://google.com

# send request to specific host
curl -iL --resolve daniu.cool:443:45.60.66.140 --resolve daniu.cool:80:45.60.66.140 https://daniu.cool
```

# Upgrade to WebSocket

```bash
curl \

--include --no-buffer \
--header "Connection: Upgrade" \
--header "Upgrade: websocket" \
--header "Host: example.com:80" \
--header "Origin: http://example.com:80" \
--header "Sec-WebSocket-Key: SGVsbG8sIHdvcmxkIQ==" \
--header "Sec-WebSocket-Version: 13" \
http://127.0.0.1/casino/5145
```

# Measure request and response times
## 1. Create a new file, curl-format.txt, and paste in:
```
     time_namelookup:  %{time_namelookup}s\n
        time_connect:  %{time_connect}s\n
     time_appconnect:  %{time_appconnect}s\n
    time_pretransfer:  %{time_pretransfer}s\n
       time_redirect:  %{time_redirect}s\n
  time_starttransfer:  %{time_starttransfer}s\n
                ----------\n
          time_total:  %{time_total}s\n
```
## 2. Make a request:
```bash
curl -w "@curl-format.txt" -o /dev/null -s "http://wordpress.com/"
```

[reference](https://stackoverflow.com/questions/18215389/how-do-i-measure-request-and-response-times-at-once-using-curl)


