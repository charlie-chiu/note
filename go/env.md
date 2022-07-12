# env
## reading environment variable using os package
```go
os.Setenv("customEnv", "customValue")

envKeys := []string{
	"customEnv",
	"GOHOSTOS",
	"PWD",
}

os.Getenv("customEnv")

for _, key := range envKeys {
	log.Printf("env key %q has the value: %v\n", key, os.Getenv(key))
}
```


## reading environment variable in .env file using godotenv package
```go
err := godotenv.Load(".env", "env_godotenv/.env")
if err != nil {
    log.Fatalf("env load fail, %v", err)
}

os.Getenv("DBUSER")
os.Getenv("DBPASS")
```
