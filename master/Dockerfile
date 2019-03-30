FROM jboss/wildfly:11.0.0.Final

COPY setup.cli /opt/jboss/wildfly/bin/

WORKDIR /opt/jboss/wildfly/bin

RUN ./add-user.sh -u admin -p 'Admin123!'
RUN ./add-user.sh -u slave -p 'Slave123!'

RUN ./jboss-cli.sh --file=setup.cli

RUN rm -rf /opt/jboss/wildfly/domain/configuration/domain_xml_history
RUN rm -rf /opt/jboss/wildfly/domain/configuration/host_xml_history

EXPOSE 9999

CMD /opt/jboss/wildfly/bin/domain.sh -b 0.0.0.0 -bmanagement 0.0.0.0
