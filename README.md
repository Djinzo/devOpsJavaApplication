Here's an improved version of your project documentation using Markdown:

---

# Tutorial: Creating Pipelines Using Local Registry, Repository, and SonarQube Server

This project is a tutorial on setting up pipelines using a local registry, repository, and a local SonarQube server.

## How to Use

1. **Change GitLab IP Address in `docker-compose.yml`**

   Update the `docker-compose.yml` file with your GitLab IP address:

   ```yaml
   hostname: '192.168.11.102'
   external_url 'http://192.168.11.102'
   ```

2. **Run Docker Compose**

   In the root directory of this project, run the following command:

   ```sh
   docker-compose up -d
   ```

3. **Access SonarQube**

   - Access SonarQube and generate a new token.
   - Add the token to your `build.gradle` file and change the SonarQube URL:

     ```gradle
     property "sonar.host.url", "http://192.168.11.102:9000"
     property "sonar.login", "sqp_2c3e28faed352398632e0c78822eec6e6d9d7472"
     ```

4. **Configure Nexus Repository**

   - Open your Nexus repository using the default username and password (`admin/admin123`).
   - Change the URL of the repo in your `build.gradle` file:

     ```gradle
     repositories {
         mavenCentral()
         maven {
             url "http://192.168.11.102:8081/nexus/content/repositories/central/"
             credentials {
                 username "admin"
                 password "admin123"
             }
             allowInsecureProtocol = true
         }
     }
     ```

5. **Setup Local GitLab**

   Ensure your local GitLab is set up, and you have a username and password. To reset the root password, run the following command:

   ```sh
   gitlab-rake "gitlab:password:reset[root]"
   ```

6. **Register GitLab Runner**

   Create a new runner in your GitLab and connect it to your `gitlab-runner` image using this command:

   ```sh
   gitlab-runner register 
   ```

7. **Push Project to GitLab**

   Once everything is set up, push the project in `devopsjavaapplication` to your local GitLab and ensure all jobs are running correctly.

---

Happy DevOps!
