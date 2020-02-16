FROM ubuntu AS build-env

RUN apt update && apt install -y wget tar build-essential git automake autoconf libtool pkg-config make g++ zlib1g-dev

ADD buildroot /opt/

RUN cd /opt && make  raspberrypi3_defconfig

RUN mkdir /opt/1 && wget  https://old.mediaarea.net/download/source/libmediainfo/19.09/libmediainfo_19.09.tar.gz -P /opt/1 && cd /opt/1 && tar -xf libmediainfo_19.09.tar.gz && rm libmediainfo_19.09.tar.gz

#RUN wget https://mediaarea.net/download/binary/libmediainfo0/19.09/libmediainfo0v5_19.09-1_amd64.xUbuntu_18.04.deb -P /opt && \
#wget https://mediaarea.net/download/binary/libmediainfo0/19.09/libmediainfo-dev_19.09-1_amd64.xUbuntu_18.04.deb -P /opt && \
#wget https://mediaarea.net/download/binary/libzen0/0.4.37/libzen0v5_0.4.37-1_amd64.xUbuntu_18.04.deb -P /opt && \
# wget https://mediaarea.net/download/binary/libzen0/0.4.37/libzen-dev_0.4.37-1_amd64.xUbuntu_18.04.deb -P  /opt && \
# cd /opt && dpkg -i libmediainfo* libzen*


#RUN cd  /opt/1/MediaInfoLib/Project/GNU/Library/ && ./autogen.sh && ./configure --enable-shared && make

FROM alpine 

COPY --from=build-env /opt /

