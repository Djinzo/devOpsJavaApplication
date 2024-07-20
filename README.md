# this project is a titural to create piplins using a local registry local repository and a local sonarQube server


how to use 


- change gitlab ip address in docker-compose.yml in your 

      hostname: '192.168.11.102'
      external_url 'http://192.168.11.102'

- in the root directory of this project run the following comande

```console
docker-compose up -d
```

- access to sonarQube and generate a new token and add it to build.gradl file change sonraQube url to 

      property "sonar.host.url", "http://192.168.11.102:9000"
      property "sonar.login", "sqp_2c3e28faed352398632e0c78822eec6e6d9d7472"
- open you nexus repositroy throw the default username and password admin admin123 and change the url of the repo in build.gradl
```java
repositories {
    mavenCentral()
    maven {
        url "http://http://192.168.11.102:8081/nexus/content/repositories/central/"
        credentials {
            username "admin"
            password "admin123"
        }
        allowInsecureProtocol = true
    }
}
```
- make sure that your local gitlab is setted up and you already have a username and password to set a usename and password run the following comand in you machine console
```console
gitlab-rake "gitlab:password:reset[root]"
```
- create a new runner in your getlab and connecte it to your gitlab-runner image using this comande

```console
gitlab-runner register 
```

once everyting is setup make push the project in devopsjavaapplication to your local gitlab


happy devOps 
