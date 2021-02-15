# GORM Arango Driver

[Arango](https://www.arangodb.com/) driver for GORM library. Checkout [gorm.io](https://gorm.io) for details.

## USAGE

```go
import (
    "gorm.io/gorm"
    arango "github.com/joselitofilho/gorm/driver/arango/pkg"
)

type User struct {
	gorm.Model
	Name  string
	Email string
}

func main() {
    db, err := gorm.Open(arango.Open(&arango.Config{}), &gorm.Config{})
    if err != nil {
        panic("failed to connect database")
    }

    // Migrate the schema
    db.AutoMigrate(&User{})

    // Create
    db.Create(&User{Name: "Joselito", Email: "joselitofilhoo@gmail.com"})

    // Read
    var user User
    db.Find(&user, "{\"ID\": 1}") // find user with ID = 1
    db.First(&user, "{\"Name\": Joselito}") // find first user with Name is Joselito
}
```

## Contributors

Checkout [Contribute](docs/CONTRIBUTING.md) for details.