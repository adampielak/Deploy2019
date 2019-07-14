#### Install
```bash
sudo apt-get install sqlite3 libsqlite3-dev
```
#### Use (Go)
```go
package main

    import (
        "database/sql"
        _ "github.com/mattn/go-sqlite3"
    )
    ```
