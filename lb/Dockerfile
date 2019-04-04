FROM haproxy

RUN apt-get update
RUN apt-get install -y locales

RUN localedef -i it_IT -c -f UTF-8 -A /usr/share/locale/locale.alias it_IT.UTF-8

ENV LANG=it_IT.UTF-8

RUN rm -f /etc/localtime

RUN ln -s /usr/share/zoneinfo/Europe/Rome /etc/localtime

RUN echo Europe/Rome > /etc/timezone

RUN echo "TZ='Europe/Rome'; export TZ" > /etc/profile.d/timezone

COPY haproxy.cfg /usr/local/etc/haproxy/
