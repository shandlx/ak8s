FROM alpine:3.18

ENV KUBELET_VERSION=v1.28.0
ENV KUBE_PROXY_VERSION=v1.28.0

RUN apk add --no-cache \
    curl && \
    curl -LO "https://dl.k8s.io/release/${KUBELET_VERSION}/bin/linux/amd64/kubelet" && \
    curl -LO "https://dl.k8s.io/release/${KUBE_PROXY_VERSION}/bin/linux/amd64/kube-proxy" && \
    chmod +x kubelet kube-proxy && \
    mv kubelet /usr/local/bin/ && \
    mv kube-proxy /usr/local/bin/ && \
    apk del curl

EXPOSE 10250

CMD ["sh"]
