## Multi stage jhipster environmet configured with ansible

spin up nexus repository with docker

`docker run -d -p 8081:8081 --name nexus sonatype/nexus:oss`

configure maven credentials into maven settings.xml 

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

