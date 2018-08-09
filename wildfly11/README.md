WildFly 11.0.0.Final with a few docker build helpers:
- WildFly can be configured with CLI scripts by using `$JBOSS-HOME/bin/jboss-cli-docker.sh`
- environment variables can be used in CLI parameter values

## Build
### Local:
```shell
docker build --tag humanswitch/wildfly11 .
```
### GitHub
```shell
docker build --tag humanswitch/wildfly11 \
  https://github.com/humanswitch/docker.git#:wildfly11
```

## Run
There is not much sense in running this empty WildFly instance. But you can do it anyway:
```shell
docker run -it --rm humanswitch/wildfly11
```

## Credits
Credits go to [Marek Goldmann](https://github.com/goldmann/wildfly-docker-configuration) for the "execute<span></span>.sh" (in this project called _jboss-cli-docker<span></span>.sh_) script which makes it possible to modify WildFly configuration easily during the Docker build process.

