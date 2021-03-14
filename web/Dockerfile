FROM golang AS build
RUN mkdir /app
WORKDIR /app
COPY dispatcher.go .
COPY static .
RUN go build dispatcher.go

FROM ubuntu AS run
RUN mkdir /app
WORKDIR /app
COPY --from=build /app/dispatcher .
EXPOSE 80
CMD ./dispatcher
