FROM jboss/wildfly:11.0.0.Final

USER root

RUN localedef -i it_IT -c -f UTF-8 -A /usr/share/locale/locale.alias it_IT.UTF-8

ENV LANG=it_IT.UTF-8

RUN rm -f /etc/localtime

RUN ln -s /usr/share/zoneinfo/Europe/Rome /etc/localtime

RUN echo Europe/Rome > /etc/timezone

RUN echo "TZ='Europe/Rome'; export TZ" > /etc/profile.d/timezone

USER jboss

COPY setup.cli /opt/jboss/wildfly/bin/

WORKDIR /opt/jboss/wildfly/bin

RUN ./add-user.sh -u admin -p 'Admin123!'
RUN ./add-user.sh -u slave -p 'Slave123!'
RUN ./add-user.sh -a -u applications -p 'Applications123!'

RUN ./jboss-cli.sh --file=setup.cli

RUN rm -rf /opt/jboss/wildfly/domain/configuration/domain_xml_history
RUN rm -rf /opt/jboss/wildfly/domain/configuration/host_xml_history

CMD /opt/jboss/wildfly/bin/domain.sh -b 0.0.0.0 -bmanagement 0.0.0.0
