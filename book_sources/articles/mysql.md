# CLI via docker container
```bash
docker run -it --rm mysql:5.7.32 mysql --host 34.92.229.26 -u root -p
```

# dump & restore
```bash
# dump
mysqldump --host 35.220.186.178 -u cdn_admin -p cdn_cdn > cdn_dns.sql

# restore
mysql -u root -p cdn_dns < cdn_dns.sql
```

# 損益查詢語法
```sql
SET @30d_ago=date_sub(CURRENT_DATE(), interval 30 day);
SET @7d_ago= date_sub(CURRENT_DATE(), interval 7 day);
SET @3d_ago= date_sub(CURRENT_DATE(), interval 3 day);
SET @1d_ago = date_sub(CURRENT_DATE(), interval 1 day);

SELECT
    `GameType`,
    SUM(`WagersTotal`) AS `d3.WagersTotal`,
    ROUND(SUM(`Payoff`) / SUM(`BetAmount`) * -100, 2) AS `d3.Profit`,
    `d7.WagersTotal`,
    `d7.Profit`,
    `d30.WagersTotal`,
    `d30.Profit`
FROM
    `FastReportDBMEM5` AS d3

LEFT JOIN
    (
        SELECT
            `GameType` as `d7.GameType`,
            SUM(`WagersTotal`) AS `d7.WagersTotal`,
            ROUND(SUM(`Payoff`) / SUM(`BetAmount`) * -100, 2) AS `d7.Profit`
        FROM
            `FastReportDBMEM5`
        WHERE
            `RoundDate` BETWEEN @7d_ago AND @1d_ago
        GROUP BY
            `GameType`
    ) as d7
ON `GameType` = `d7.GameType`

LEFT JOIN
    (
        SELECT
            `GameType` as `d30.GameType`,
            SUM(`WagersTotal`) AS `d30.WagersTotal`,
            ROUND(SUM(`Payoff`) / SUM(`BetAmount`) * -100, 2) AS `d30.Profit`
        FROM
            `FastReportDBMEM5`
        WHERE
            `RoundDate` BETWEEN @30d_ago AND @1d_ago
        GROUP BY
            `GameType`
    ) as d30
ON `GameType` = `d30.GameType`

WHERE
    `RoundDate` BETWEEN @3d_ago AND @1d_ago AND `GameType` != 5888
GROUP BY
    `GameType`
HAVING
    `d3.Profit` < 1
ORDER BY
    `d3.Profit` ASC
```