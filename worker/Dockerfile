FROM alpine:3.18 AS builder
ENV KUBELET_VERSION=v1.28.0
ENV KUBE_PROXY_VERSION=v1.28.0
RUN apk add --no-cache curl upx binutils gcc libc-dev musl-dev && \
    curl -LO "https://dl.k8s.io/release/${KUBELET_VERSION}/bin/linux/amd64/kubelet" && \
    curl -LO "https://dl.k8s.io/release/${KUBE_PROXY_VERSION}/bin/linux/amd64/kube-proxy" && \
    chmod +x kubelet kube-proxy && \
    strip kubelet kube-proxy && \
    upx --best --lzma kubelet kube-proxy && \
    rm -rf /var/cache/apk/*

FROM scratch
COPY --from=builder /kubelet /kube-proxy /
EXPOSE 10250
CMD ["/kubelet"]
