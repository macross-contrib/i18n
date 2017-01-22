# i18n

Middleware i18n provides app Internationalization and Localization for [Macross](https://github.com/insionng/macross).

### Installation

	go get -u github.com/macross-contrib/i18n

## Test

```go
package main

import (
	"github.com/insionng/macross"
	"github.com/macross-contrib/i18n"
)

func main() {
	m := macross.Classic()
	m.Use(i18n.I18n(i18n.Options{
		Directory: "locale",
		Langs:     []string{"en-US", "zh-CN"},
		Names:     []string{"English", "简体中文"},
	}))

	m.Get("/", func(self *macross.Context) error {
		return self.String("current language is " + self.Locale.Language())
	})

	// Use in handler.
	m.Get("/trans", func(self *macross.Context) error {
		return self.String(self.Locale.Tr("hello %s", "world"))
	})

	m.Listen(9999)
}
```

## Getting Help

- [API Reference](https://gowalker.org/github.com/macross-contrib/i18n)

## License

This project is under the Apache License, Version 2.0. See the [LICENSE](LICENSE) file for the full license text.
