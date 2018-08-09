WildFly 11.0.0.Final with:
- Keycloak WildFly adapter

   to provide OIDC support.  
- MySQL xa-datasource support

   by installing and configuring the MySQL 5.1.46 JDBC driver. It also provides in a WildFly cli script `add-xa-datasource.cli` which can be used in child images.

## Build
### Local
```shell
docker build --tag humanswitch/wildfly11-keycloak-adapter-mysql-driver .
```
### GitHub
```shell
docker build --tag humanswitch/wildfly11-mysql-driver https://github.com/humanswitch/docker.git#:wildfly11-mysql-driver
```

## Run
Not much sense in running this empty WildFly instance. But you can do it anyway:
```shell
docker run -it --rm humanswitch/wildfly11-keycloak-adapter-mysql-driver
```