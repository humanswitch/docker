WildFly 11.0.0.Final with:
- Keycloak WildFly adapter
- MySQL xa-datasource support
- base support for HumanSwitch JEE applications

    WildFly CLI script which will add HumanSwitch application system property and will configure reverse proxy support on port 8080 (http).

## Build and run
1. put both _Dockerfile_ of this project and the applications web archive in the same folder
2. create a _docker-compose.yaml_ with specific application configuration
3. use `docker-compose up` for building and running the application

### Docker Compose
This image requires to bind an application folder to `/srv/humanswitch-app`.

Expected arguments:

 Argument | Description 
--- | ---
HS_APP_NAME | Name of the application
HS_APP_DEPLOYFILENAME | Name of the web archive to be deployed. This file should be available in the build context.
DS_SERVERNAME | Hostname of the MySQL service which contains the application's database
DS_USER_NAME | MySQL login name
DS_PASSWORD | MySQL password
DS_DATABASENAME | MySQL database name


#### Example _docker-compose.yaml_
```yaml
version: '3.1'

services:

  myapp:
    container_name: myapp
    restart: always
    ports:
      - 8080:8080
    volumes:
      - /srv/iqnomy/myapp/:/srv/humanswitch-app/
    build: 
      context: .
      args:
        HS_APP_NAME: myapp
        HS_APP_DEPLOYFILENAME: myapp.war
        DS_SERVERNAME: mysql.local
        DS_USER_NAME: myapp
        DS_PASSWORD: myapp_secret
        DS_DATABASENAME: myapp
```
