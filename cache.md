# Go cache invalidation

An attempt to use the migrated v2 code of module moda in some other code failed. Go cache invalidation to the rescue

## checksum mismatch

```console
go get -u -v ./...
go: downloading github.com/tullo/moda/v2 v2.0.0
verifying github.com/tullo/moda/v2@v2.0.0: checksum mismatch
	downloaded: h1:kj/Nnt+5f304JHZfd0MoRM5dokUZs/3C+LDUk7dEaKg=
	go.sum:     h1:KNESmlMaJMSZQ/11falQtef0IlnmxxH/hlIP/Zcx98k=
```

## Solution: go cache cleanup

```console
rm go.sum
go clean -modcache
go get -u -v ./...
go mod tidy
go build ./...
go test ./...
```
