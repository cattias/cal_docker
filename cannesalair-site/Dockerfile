FROM ubuntu:latest
MAINTAINER "Kiki & Toto"

VOLUME ['/cannesalair']

RUN apt-get -y update
RUN apt-get -y install libjpeg-dev libfreetype6-dev zlib1g-dev python-imaging python-pip python-dev libevent-dev python-distribute libmysqlclient-dev

ADD ./cannesalair/requirements.txt /cannesalair/requirements.txt

RUN ln -s /usr/lib/`uname -i`-linux-gnu/libfreetype.so /usr/lib/
RUN ln -s /usr/lib/`uname -i`-linux-gnu/libjpeg.so /usr/lib/
RUN ln -s /usr/lib/`uname -i`-linux-gnu/libz.so /usr/lib/
RUN ln -s /usr/include/freetype2 /usr/include/freetype

RUN pip install -r /cannesalair/requirements.txt
RUN easy_install -U Djblets==0.6.18

WORKDIR /cannesalair

EXPOSE 9005
ENTRYPOINT gunicorn_django -b 0.0.0.0:9005

#CMD python manage.py runserver 0.0.0.0:9005

