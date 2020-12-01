## We specify the base image we need for our
## go application
FROM golang:onbuild AS build

## We create an /app directory within our
## image that will hold our application source
## files
RUN mkdir /app
## We copy everything in the root directory
## into our /app directory
ADD . /app
## We specify that we now wish to execute
## any further commands inside our /app
## directory
WORKDIR /app
## we run go build to compile the binary
## executable of our Go program
RUN go build -o main .
## Our start command which kicks off
## our newly created binary executable
CMD ["/app/main"]

## the lightweight scratch image we'll
## run our application within
FROM scratch AS production
## We have to copy the output from our
## builder stage to our production stage
COPY --from=build /app .
## we can then kick off our newly compiled
## binary exectuable!!
CMD ["./main"]