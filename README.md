# fxslog

[![MIT License](https://img.shields.io/github/license/ipfans/fxslog)](https://github.com/ipfans/fxslog/blob/main/LICENSE)
[![GoDoc](http://godoc.org/github.com/ipfans/fxslog?status.svg)](http://godoc.org/github.com/ipfans/fxslog)
[![GitHub release](https://img.shields.io/github/v/release/ipfans/fxslog)](https://github.com/ipfans/fxslog/releases)
[![GitHub go.mod Go version](https://img.shields.io/github/go-mod/go-version/ipfans/fxslog)](https://github.com/ipfans/fxslog/blob/main/go.mod)
[![Go Report Card](https://goreportcard.com/badge/github.com/ipfans/fxslog)](https://goreportcard.com/report/github.com/ipfans/fxslog)
[![Issues](https://img.shields.io/github/issues/ipfans/fxslog)](https://github.com/ipfans/fxslog/issues)

Integration slog with `uber-go/fx`.

## HOWTO

```go
	app := fx.New(
		fx.Provide(func() *slog.Logger {
			return slog.New(slog.NewJSONHandler(os.Stdout))
		}),
		fx.WithLogger(func(logger *slog.Logger) fxevent.Logger {
			return fxslog.New(logger)
		}),
	)
	defer app.Stop(context.TODO())
	app.Start(context.TODO())
```
