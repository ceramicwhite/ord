ARG VERSION=0.5.1

ARG GOTTY_VERSION=v1.5.0

FROM rust:1-bullseye AS builder

ARG VERSION

WORKDIR /ord
RUN git clone -b $VERSION https://github.com/casey/ord.git .
RUN cargo build --release

FROM debian:bullseye-slim

RUN  adduser --disabled-password --uid 1000 --home /data --gecos "" ordinal

USER ordinal

WORKDIR /data

COPY --from=builder /ord/target/release/ord /bin/ord

CMD ["ord"]