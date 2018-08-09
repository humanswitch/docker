WildFly 11.0.0.Final with the Keycloak WildFly adapter to provide OIDC support.

## Build
```shell
docker build --tag humanswitch/wildfly11-keycloak-adapter .
```

## Run
Not much sense in running this empty WildFly instance. But you can do it anyway:
```shell
docker run -it --rm humanswitch/wildfly11-keycloak-adapter
```