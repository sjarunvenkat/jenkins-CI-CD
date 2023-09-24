## CI/CD Pipeline Setup Using Jenkins

### Prerequisites

Before you begin, ensure you have the following prerequisites:

- A Jenkins server installed and configured.
- Your sample application's source code hosted in a version control system like Git (e.g., GitHub).
- Docker installed on the Jenkins server.
- Necessary plugins installed in Jenkins (e.g., Git Plugin, Docker Plugin).

### Step 1: Create a New Jenkins Job

![image](https://github.com/sjarunvenkat/jenkins-CI-CD/assets/73863663/d50b6659-b046-402e-a3a6-df49f0991ef4)


1. Log in to your Jenkins dashboard.

2. Click on "New Item" to create a new Jenkins job.

3. Enter a name for your job (e.g., "MySampleApp-CI/CD") and select "Freestyle project."

4. Click "OK" to create the job.

### Step 2: Configure the Source Code Repository

![image](https://github.com/sjarunvenkat/jenkins-CI-CD/assets/73863663/d3e6b1ec-9a95-4b47-a068-0d54c9f985ff)

1. In the job configuration, scroll down to the "Source Code Management" section.

2. Select your version control system (e.g., Git).

3. Provide the repository URL (e.g., https://github.com/sjarunvenkat/server-management-web.git).

![image](https://github.com/sjarunvenkat/jenkins-CI-CD/assets/73863663/166a904f-25c6-4562-8d9e-006138c45d2c)

4. Set up credentials if needed, especially if the repository is private.

5. Choose the branch you want to build (e.g., "main").

### Step 3: Configure the Build Step

![image](https://github.com/sjarunvenkat/jenkins-CI-CD/assets/73863663/efb5a4af-3c8f-4814-b014-dc7bcefa1b45)

1. Scroll down to the "Build" section.

2. Click on "Add build step" and select "Invoke top-level Maven targets."

3. In the "Goals" field, enter clean install. This will build your Java application using Maven.

   ```shell
   -f mongoserver_formui/pom.xml clean install
   ```

### Step 4: Configure Docker Build and Publish

![image](https://github.com/sjarunvenkat/jenkins-CI-CD/assets/73863663/8d15724d-28ee-45ef-b537-29ed38392b24)


1. In the same "Build Actions" section. Click on "Build action" and choose "Docker Build and Publish." 

2. Configure the Docker Build and Publish settings:

   - **Repository Name:** Specify the name of the Docker repository (e.g., yourdockerhubusername/my-sample-app).
   - **Tag:** Set a tag for the Docker image (e.g., "latest").
   - **Docker Host URI:** Leave it empty if Docker is running locally. Otherwise, specify the Docker host URI.
   - **Registry Credentials:** If needed, configure credentials for the Docker registry.

### Step 5: Save and Run the Job

![image](https://github.com/sjarunvenkat/jenkins-CI-CD/assets/73863663/8baca2a6-1309-4db9-b646-e9f8945a103c)

1. Click "Save" to save your Jenkins job configuration.

2. Trigger a build manually by clicking "Build Now."

3. Observe the build process in the Jenkins console output. It should fetch your source code, build your application, and create a Docker image.

![image](https://github.com/sjarunvenkat/jenkins-CI-CD/assets/73863663/68e11f21-1811-47dc-8aee-09bc36fb41c1)

### Step 6: Verify the Docker Image

1. Log in to your Docker registry (e.g., Docker Hub) and verify that the Docker image was pushed successfully.


### Conclusion
You have successfully set up a CI/CD pipeline using Jenkins for your sample application. Whenever changes are pushed to your repository, Jenkins will automatically trigger builds and, if configured, deployments.
