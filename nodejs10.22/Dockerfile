# 基础镜像
# 包含了必要的系统软件包和安装的 npm 依赖包
FROM node:10.22.1-stretch-slim
LABEL maintainer="inspur-fcs"
RUN set -ex; \
    apt-get update; \
    apt-get install -y --no-install-recommends \
        curl telnet iputils-ping vim-tiny iproute2 dos2unix file ca-certificates tzdata openssl procps; \
    apt-get clean; \
    rm -rf /var/lib/apt/lists/*;

# 安装ffmpeg
RUN echo "deb [check-valid-until=no] http://archive.debian.org/debian jessie-backports main" > /etc/apt/sources.list.d/jessie-backports.list
RUN sed -i '/deb http:\/\/deb.debian.org\/debian jessie-updates main/d' /etc/apt/sources.list
RUN apt-get -o Acquire::Check-Valid-Until=false update
RUN apt-get -y --force-yes install yasm ffmpeg

RUN set -ex; \
    # https://www.npmjs.com
    npm install --global --unsafe-perm --registry http://registry.npm.taobao.org \
                express@4.17.1; \
    npm install --global --unsafe-perm --registry http://registry.npm.taobao.org \
               jwt-decode@3.1.2; \
    npm install --global --unsafe-perm --registry http://registry.npm.taobao.org \
               uuid@8.3.2; \
    npm cache clean --force;
