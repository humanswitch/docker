FROM humanswitch/wildfly11-keycloak-adapter-mysql-driver:latest

ADD *.cli $JBOSS_HOME/bin/

ARG HS_APP_NAME
ARG HS_APP_DEPLOYFILENAME=${HS_APP_NAME}.war
ARG DS_NAME=${HS_APP_NAME}DS
ARG DS_JNDI_NAME=java:/${HS_APP_NAME}DS
ARG DS_DATABASENAME=${HS_APP_NAME}
ARG DS_SERVERNAME
ARG DS_USER_NAME
ARG DS_PASSWORD

USER root

# Add application specific datasource
RUN $JBOSS_HOME/bin/jboss-cli-docker.sh $JBOSS_HOME/bin/add-xa-datasource.cli

# Add application specific environement variables
RUN $JBOSS_HOME/bin/jboss-cli-docker.sh $JBOSS_HOME/bin/application.cli

# Install application
ADD ${HS_APP_DEPLOYFILENAME} $JBOSS_HOME/standalone/deployments/

# Cleanup
RUN rm -rf $JBOSS_HOME/standalone/configuration/standalone_xml_history/current \
    && chown -R jboss:0 ${JBOSS_HOME} \
    && chmod -R g+rw ${JBOSS_HOME}