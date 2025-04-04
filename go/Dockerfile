ARG GO_VERSION=1.24
ARG GOSEC_VERSION=2.22.3

FROM securego/gosec:${GOSEC_VERSION} AS gosec

FROM golang:${GO_VERSION}-alpine

ARG GODOC_VERSION=latest
ARG GOJUNIT_VERSION=latest
ARG GOLANGCI_LINT_VERSION=v2.0.2

RUN apk update && apk add git && rm -rf /var/cache/apk/*

RUN    go install golang.org/x/tools/cmd/godoc@${GODOC_VERSION} \
    && go install github.com/jstemmer/go-junit-report@${GOJUNIT_VERSION} \
    && wget -O- -nv https://raw.githubusercontent.com/golangci/golangci-lint/${GOLANGCI_LINT_VERSION}/install.sh | sh \
    ;

COPY --from=gosec /bin/gosec /go/bin/gosec

ADD ./run-toolset /go/bin/run-toolset

CMD ["run-toolset"]
