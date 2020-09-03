FROM mamohr/centos-java
LABEL MAINTAINER="chengmangmang@gmail.com" VERSION="1.0.0" BUILD_DATE="2020-09-01" \
      RESOURCES="https://github.com/tesseract-ocr/tesserac http://www.leptonica.org/index.html https://github.com/tesseract-ocr/tessdata" \
      DESCRIPTION="This image integrated and edited the running environment of tesseract-4.1.1 and leptonica-1.80.0, \
      and made it based on CentOS system. Based on this basic image, you can run your own tess4j jar application"

# env(tesseract)
ENV LD_LIBRARY_PATH="/usr/local/lib" \
    LIBLEPT_HEADERSDIR="/usr/local/include" \
    PKG_CONFIG_PATH="/usr/local/lib/pkgconfig"
# install  tesseract
ADD   tesseract-4.1.1.tar.gz /
ADD   leptonica-1.80.0.tar.gz /

RUN   yum -y install file automake libicu-devel libpango1.0-dev libcairo-dev libjpeg-devel libpng-devel libtiff-devel zlib-devel libtool gcc-c++ make \
      && cd /leptonica-1.80.0 && ./configure && make && make install \
      && cd /tesseract-4.1.1 && ./autogen.sh && ./configure && make && make install \
      && rm -rf /leptonica-1.80.0 /tesseract-4.1.1
# set timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN echo 'Asia/Shanghai' >/etc/timezone