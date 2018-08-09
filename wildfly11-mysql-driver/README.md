WildFly 11.0.0.Final with MySQL xa-datasource support, by installing and configuring the MySQL 5.1.46 JDBC driver. It also provides in a WildFly cli script `add-xa-datasource.cli` which can be used in child images.

## Build
### Local
```shell
docker build --tag humanswitch/wildfly11-mysql-driver .
```
### GitHub
```shell
docker build --tag humanswitch/wildfly11-mysql-driver https://github.com/humanswitch/docker.git#:wildfly11-mysql-driver
```

## Usage
Example:
```docker
FROM humanswitch/wildfly11-mysql-driver:latest

ENV DS_NAME exampleDS
ENV DS_JNDI_NAME java:/exampleDS
ENV DS_SERVERNAME mysql.mycompany.local
ENV DS_USER_NAME exampleuser
ENV DS_PASSWORD secret
ENV DS_DATABASENAME example

RUN $JBOSS_HOME/bin/jboss-cli-docker.sh $JBOSS_HOME/bin/add-xa-datasource.cli
...
```

## Run
Not much sense in running this empty WildFly instance. But you can do it anyway:
```shell
docker run -it --rm humanswitch/wildfly11-mysql-driver
```