FROM mcr.microsoft.com/vscode/devcontainers/universal:linux

USER root

# install nginx
RUN apt-get upgrade -yy && \
    apt-get update && \
    apt-get install curl build-essential -yy && \
    apt-get install -yy curl gnupg2 ca-certificates lsb-release && \
    echo "deb http://nginx.org/packages/debian `lsb_release -cs` nginx" \
    | tee /etc/apt/sources.list.d/nginx.list && \
    curl -fsSL https://nginx.org/keys/nginx_signing.key | apt-key add - && \
    apt-key fingerprint ABF5BD827BD9BF62 && \
    apt-get update -yy && \
    apt-get install nginx -yy && \
    apt-get install libcap2-bin -yy && \
    setcap CAP_NET_BIND_SERVICE=+eip /usr/sbin/nginx

USER codespace

ENV PATH="/home/codespace/.npm-global/bin:${PATH}"

RUN npm install -g @abtnode/cli@latest
