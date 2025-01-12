# Use Alpine Linux as the base image
FROM alpine:latest

# Set environment variables
ENV KUBELET_VERSION=v1.28.0
ENV KUBE_PROXY_VERSION=v1.28.0

# Install necessary packages
RUN apk update && apk add --no-cache \
    bash \
    curl \
    iproute2 \
    iptables \
    openrc \
    ca-certificates \
    coreutils \
    ebtables \
    ip6tables

# Install kubelet (for managing pods)
RUN curl -LO "https://dl.k8s.io/release/${KUBELET_VERSION}/bin/linux/amd64/kubelet" && \
    chmod +x kubelet && \
    mv kubelet /usr/local/bin/kubelet

# Install kube-proxy (for networking)
RUN curl -LO "https://dl.k8s.io/release/${KUBE_PROXY_VERSION}/bin/linux/amd64/kube-proxy" && \
    chmod +x kube-proxy && \
    mv kube-proxy /usr/local/bin/kube-proxy

# Expose necessary ports for communication
EXPOSE 10250

# Set the default command to bash
CMD ["bash"]
