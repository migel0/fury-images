ARG MONGO

FROM golang:1.12 AS builder

RUN git clone https://github.com/kubernetes/apimachinery.git \
      /go/src/k8s.io/apimachinery

COPY ./peer-finder.go /src/kubernetes-retired/contrib/peer-finder/

WORKDIR /src/kubernetes-retired/contrib/peer-finder

RUN CGO_ENABLED=0 go build -a -installsuffix cgo --ldflags '-w' ./peer-finder.go

FROM mongo:${MONGO}

COPY --from=builder /src/kubernetes-retired/contrib/peer-finder/peer-finder /usr/bin/peer-finder

ENTRYPOINT ["/usr/bin/peer-finder"]

CMD ["-h"]
