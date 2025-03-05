# go-toolset

A Docker image containing Go and a small set of tools:

* git
* [golangci-lint](https://github.com/golangci/golangci-lint)
* [godoc](https://github.com/golang/tools/tree/master/godoc)
* [gosec](https://github.com/securego/gosec)
* [go-junit-report](https://github.com/jstemmer/go-junit-report)

To run the default tools, call Docker as follows:

```
docker run -v <local-project-dir>:<project-dir> -w <project-dir> robtimus/go-toolset
```

This will run:

* `go get .` to install all dependencies
* `go vet`
* `golangci-lint run`
* `go build`
* `go test`
* `gosec`

To serve godoc on port 9001, call Docker as follows:

```
docker run -v <local-project-dir>:<project-dir> -w <project-dir> -p 9001:9001 robtimus/go-toolset godoc -http=:9001
```
