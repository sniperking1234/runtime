# 基础镜像
# 包含了必要的系统软件包
FROM openjdk:8-jdk-slim-stretch
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
