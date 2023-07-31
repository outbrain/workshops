# syntax=docker/dockerfile:1

FROM ubuntu:22.04 AS build

# Combine installing packages into a one-liner, producing only one
# image layer. Otherwise the update and cleanup will both make the
# image bigger for no good reason.
# Having update in a separate line is not a good idea either, because
# consecutive runs will simply take the cached layer and not really
# update apt sources.
# Sometimes it makes sense to pin the version of individual packets...
RUN apt-get update && apt-get install -y \
  build-essential \
  && apt-get clean && rm -rf /var/lib/apt/lists/*

# Copying is done here, since it is likely that we will update the source
# often, and the packages installed above not so much. Thus we preserve
# the layer/cache of the installation above even when we change the source.
COPY hello.c /
RUN make hello
CMD /hello

FROM ubuntu:22.04
LABEL "com.outbrain.vendor"="Outbrain"
LABEL version="1.0"

COPY --from=build /hello /hello
CMD /hello
