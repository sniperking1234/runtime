# 基础镜像
# 包含了必要的系统软件包和安装的 Python 依赖包
FROM python:2.7.18-slim-stretch
LABEL maintainer="inspur-fcs"
RUN set -ex; \
    apt-get update; \
    apt-get install -y --no-install-recommends \
        curl telnet iputils-ping vim-tiny iproute2 dos2unix file ca-certificates tzdata openssl procps \
        default-libmysqlclient-dev gcc; \
    apt-get clean; \
    rm -rf /var/lib/apt/lists/*;

# 安装ffmpeg
RUN echo "deb [check-valid-until=no] http://archive.debian.org/debian jessie-backports main" > /etc/apt/sources.list.d/jessie-backports.list
RUN sed -i '/deb http:\/\/deb.debian.org\/debian jessie-updates main/d' /etc/apt/sources.list
RUN apt-get -o Acquire::Check-Valid-Until=false update
RUN apt-get -y --force-yes install yasm ffmpeg

RUN set -ex; \
    # https://pypi.org
    pip install --no-cache-dir -U pip setuptools; \
    pip install --no-cache-dir Flask==1.1.2 \
                               pipdeptree==1.0.0 \
                               Cython==0.29.21; \
    pip install --no-cache-dir numpy==1.16.1; \
    pip install --no-cache-dir tensorflow==1.15.0; \
    # AI, ML, DL, Big Data, NLP, Image Processing etc.
    pip install --no-cache-dir gensim==3.8.3 \
                               hyperopt==0.2.5 \
                               imbalanced-learn==0.4.3 \
                               jieba==0.42.1 \
                               Keras==2.4.3 \
                               opencv-python==4.2.0.32 \
                               pydotplus==2.0.2 \
                               scikit-image==0.14.5 \
                               scikit-surprise==1.1.1 \
                               Scrapy==1.8.0 \
                               seaborn==0.9.1 \
                               Wand==0.6.4 \
                               xgboost==0.82; \
    # Database
    pip install --no-cache-dir mysqlclient==1.4.6 \
                               PyMySQL==0.10.1 \
                               SQLAlchemy==1.3.20 \
                               redis==3.5.3 \
                               psycopg2-binary==2.8.6 \
                               cx-Oracle==7.3.0 \
                               elasticsearch==7.10.0 \
                               py2neo==2020.1.1; \
    # Excel
    pip install --no-cache-dir xlrd==1.2.0 \
                               xlwt==1.3.0; \
    # Data parse
    pip install --no-cache-dir dateparser==0.7.6 \
                               dicttoxml==1.7.4 \
                               docutils==0.16 \
                               html5lib==1.1 \
                               iniparse==0.5 \
                               simplejson==3.17.2 \
                               tbb4py==2019.0; \
    # Data interchange
    pip install --no-cache-dir cbor==1.0.0 \
                               cprotobuf==0.1.10 \
                               crcmod==1.7 \
                               lz4==2.2.1; \
    # Security
    pip install --no-cache-dir asn1crypto==1.4.0 \
                               pycrypto==2.6.1 \
                               pycryptodome==3.9.9; \
    # Network
    pip install --no-cache-dir httplib2==0.18.1 \
                               requests==2.25.0;\
    # Jwt
    pip install --no-cache-dir python_jwt==2.0.1;
