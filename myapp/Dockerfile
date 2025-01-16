# Stage 1: Build the Go application
FROM golang:1.19 AS build

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . ./
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o myapp

# Stage 2: Create the final image
FROM scratch

COPY --from=build /app/myapp /myapp

ENTRYPOINT ["/myapp"]
