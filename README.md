## Multi stage jhipster environment configured with ansible

### What it does
- jhipster pom modified to deploy artifacts to maven
- ansible playbook to install and configure a mariadb database
- ansible playbook to install jhipster app as systemctl (directly from maven)
- ansible directory structure for multi stage environment

### To Do
- improving multi stage environment configuration
- add reverse proxy/load balancing features
- use ansible vault

### Steps

spin up nexus repository

`docker run -d -p 8081:8081 --name nexus sonatype/nexus:oss`

configure maven credentials into your maven settings.xml 

```
<server>
  <id>maven.localhost</id>
  <username>admin</username>
  <password>admin123</password>
</server>
```

build jhipster app and upload it to maven

`cd jhipster-app && ./mvnw -Pprod deploy -DskipTests=true`

run vagrant

`vagrant up`

configure database 

`ansible-playbook -i environments/local database.yml`

configure jhipster app

`ansible-playbook -i environments/local jhipster.yml`

got to `http://localhost:8080`


Useful links:

https://www.digitalocean.com/community/tutorials/how-to-manage-multistage-environments-with-ansible

