# Specify the version as a build argument
ARG GLEAM_VERSION="v1.3.2"

# Builder stage. We use multi-stage builds to make the image slimmer.
FROM alpine:latest AS builder
# Repeated, because it won't propagate otherwise.
ARG GLEAM_VERSION
ENV VERSION=${GLEAM_VERSION}
# Install required packages for building
RUN apk add git rust cargo

# Setup repository
RUN mkdir /work
WORKDIR /work
RUN git clone https://github.com/gleam-lang/gleam.git
WORKDIR /work/gleam

# Build required version
RUN git checkout $VERSION
RUN cargo build --release

# Runner stage
# Install Erlang, which is needed to run Gleam programs (OTP)

FROM erlang:27-alpine AS runner

# Copy the built executable and any necessary libraries from the builder stage
COPY --from=builder /work/gleam/target/release/gleam /usr/bin/gleam
COPY --from=builder /work/gleam/target/release/libgleam_wasm.so /usr/lib/libgleam_wasm.so

# Set the default entrypoint to the Gleam executable
CMD ["/usr/bin/gleam"]