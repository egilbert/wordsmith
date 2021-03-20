FROM golang AS build
RUN mkdir /app
WORKDIR /app
COPY dispatcher.go .
RUN go build dispatcher.go

FROM ubuntu AS run
RUN mkdir /app
WORKDIR /app
COPY --from=build /app/dispatcher .
COPY static ./static
EXPOSE 80
CMD ./dispatcher
