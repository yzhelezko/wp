FROM alpine:3.11

ENV KUBE_LATEST_VERSION="v1.18.8"
ENV HELM_VERSION="v3.3.1"

RUN apk add --no-cache ca-certificates bash git openssh curl ansible python3 zip unzip \
    && wget -q https://storage.googleapis.com/kubernetes-release/release/${KUBE_LATEST_VERSION}/bin/linux/amd64/kubectl -O /usr/local/bin/kubectl \
    && chmod +x /usr/local/bin/kubectl \
    && wget -q https://get.helm.sh/helm-${HELM_VERSION}-linux-amd64.tar.gz -O - | tar -xzO linux-amd64/helm > /usr/local/bin/helm \
    && chmod +x /usr/local/bin/helm \
    && chmod g+rwx /root \
    && mkdir /config \
    && chmod g+rwx /config \
    && pip3 install openshift PyYAML jmespath \
    && ansible-galaxy collection install community.kubernetes -p /usr/share/ansible/collections

WORKDIR /config

CMD bash
