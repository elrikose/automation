# Necessary tools to install an AWS EKS cluster. After installing, all you must do is run to authenticate with AWS 
FROM openjdk:8-slim

# Git / CURL / jq
RUN apt-get update \ 
    && apt-get -y install git curl jq vim awscli \
    && rm -rf /var/lib/apt/lists/*

# EKSCTL
RUN curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp \
    && mv /tmp/eksctl /usr/local/bin

# ECS-CLI
RUN curl -Lo /usr/local/bin/ecs-cli https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-linux-amd64-latest \
    && chmod +x /usr/local/bin/ecs-cli

# Kubens / Kubectx
RUN git clone https://github.com/ahmetb/kubectx /opt/kubectx \
    && chmod +x /opt/kubectx/kubens /opt/kubectx/kubectx \
    && ln -s /opt/kubectx/kubectx /usr/local/bin/kubectx \
    && ln -s /opt/kubectx/kubens /usr/local/bin/kubens

# Helm
RUN curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 \
    && chmod 700 get_helm.sh \
    && ./get_helm.sh

