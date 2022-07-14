# MySQL
## SELECT multi rows
```go
c := mysql.Config{
	User:                 os.Getenv("MYSQL_USER"),
	Passwd:               os.Getenv("MYSQL_PASS"),
	Net:                  "tcp",
	Addr:                 os.Getenv("WAGERS_DB5_ALL"),
	DBName:               "WagersDB5_All",
	AllowNativePasswords: true,
}
// get a sql connection
conn, _ := sql.Open("mysql", c.FormatDSN())

rows, _ := conn.Query("SELECT `WagersID`, `BetAmount`, `Payoff`  FROM `Wagers` WHERE `GameType` = 5186 ORDER BY `Wagers`.`RoundDate` DESC LIMIT ?", limit)

for rows.Next() {
	row := Wager{}
	err := rows.Scan(&row.WagersID, &row.BetAmount, &row.Payoff)
	wagers = append(wagers, row)
}
```

## dump columns
```go
func main() {
	log.SetFlags(log.Lshortfile + log.Ltime)
	//log.Println("mysql")

	const DBUser = "dragonborn"
	const DBPassword = "fus_ro_dah"
	cfg := &mysql.Config{
		User:                 DBUser,
		Passwd:               DBPassword,
		Net:                  "tcp",
		Addr:                 "192.168.141.62",
		DBName:               "WagersDB5_All",
		AllowNativePasswords: true,
	}
	db, err := sql.Open("mysql", cfg.FormatDSN())
	if err != nil {
		log.Fatalf("db open error, %v", err)
	}
	defer db.Close()

	rows, err := db.Query("SELECT WagersID, BetAmount, Payoff FROM Wagers LIMIT 30")
	if err != nil {
		log.Fatalf("db.query error %v", err)
	}

	cols, err := rows.Columns()
	if err != nil {
		fmt.Println("Failed to get columns", err)
		return
	}

	// Result is your slice string.
	rawResult := make([][]byte, len(cols))
	result := make(map[string]string, len(cols))

	dest := make([]interface{}, len(cols)) // A temporary interface{} slice
	for i, _ := range rawResult {
		dest[i] = &rawResult[i] // Put pointers to each string in the interface slice
	}

	for rows.Next() {
		err = rows.Scan(dest...)
		if err != nil {
			fmt.Println("Failed to scan row", err)
			return
		}

		for i, raw := range rawResult {
			colName := cols[i]
			if raw == nil {
				result[colName] = "\\N"
			} else {
				result[colName] = string(raw)
			}
		}

		fmt.Printf("%+v\n", result)
	}
}
```
