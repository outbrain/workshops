FROM ubuntu AS build
# We are copying local file into the image
COPY hello.c /
RUN apt-get update
RUN apt-get install -y build-essential
RUN make hello
# Idealy we run some simple tests here as well
CMD /hello

# Now start from a fresh ubuntu image, without
# any not needed source code or build tools installed
FROM ubuntu
# Copy the built binary from the previous image,
# since this is the only thing we need!
COPY --from=build /hello /hello
CMD /hello
