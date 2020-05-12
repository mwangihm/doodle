FROM golang:1.11 AS builder
RUN apk add --no-cache git
RUN go get github.com/pdevine/go-asciisprite
COPY cheers.go .
RUN CGO_ENABLED=0 GOOS=linux go build -a -ldflags '-extldflags "-static"' -o cheers cheers.go

FROM scratch
COPY --from=builder /project/cheers /cheers
ENTRYPOINT ["/cheers"]
