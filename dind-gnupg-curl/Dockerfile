ARG DIND

FROM busybox as downloader
RUN wget https://github.com/theupdateframework/notary/releases/download/v0.6.1/notary-Linux-amd64
RUN chmod +x notary-Linux-amd64

FROM docker:${DIND}-dind

RUN apk add --no-cache gnupg curl
COPY --from=downloader notary-Linux-amd64 /bin/notary
