# show distribution

```bash
cat /etc/*-release
```

# find file

```bash
find . -name [file_name]
```

# grep

```bash
grep pattern filename
grep -Rn "keyword" *
```

-v 反向搜尋 (排除找到的)
-R recursive
-n with line number

# clear file contents

```bash
> filename
```
PS: If you need sudo call, please consider to use truncate as answered here.

[linux - How to clear the contents of a file from the command line? - Super User](https://superuser.com/questions/90008/how-to-clear-the-contents-of-a-file-from-the-command-line)

# rm - batch remove with prompt

```bash
rm -i name_pattern*
```

# du - disk usage

```bash
du -h --max-depth=1
```

# nohup (no hang up)

```bash
#basic
nohup php -f play.php &

# to log file
nohup $COMMAND > logfile

# with env
env PORT=8088 nohup ./pong &
```

# 對遠端主機執行指令

```bash
ssh {host} {command} ...

#!/bin/bash
#flash2DB disk usage check

hosts=`cat flash2DB_list`
for host in $hosts
do
    if [[ $host == *"#"* ]]; then
       continue
    fi
    echo "checking $host ..."
    ssh $host df -h | sed 's/%/ %/' | awk 'NR!=1{if ($5 >= 50) {print $0}}' | sed 's/ %/%/'
done
```