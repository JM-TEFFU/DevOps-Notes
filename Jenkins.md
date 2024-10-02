# 🚀 What is Jenkins?

Jenkins is an open source automation tool written in Java with plugins built for contiouns integration process. Jenkins is used to build, test and deplo your software projects continously and it intgrates changes to the project continously. So it also known as CI/CD tool. There are other similar tools in the market but Jenkins stands out with its vast plugin collection, easily configurable and course it is free of cost.

![jenkins](https://github.com/user-attachments/assets/5a0d32a2-13ef-4c4d-8917-e4dc74013c1f)


# What can Jenkins do?

1. 𝗖𝗼𝗻𝘁𝗶𝗻𝘂𝗼𝘂𝘀 𝗶𝗻𝘁𝗲𝗴𝗿𝗮𝘁𝗶𝗼𝗻: Jenkins automatically builds and tests your code every time a developer commits changes, ensuring quick feedback and fewer integration issues.
2. 𝗖𝗼𝗻𝘁𝗶𝗻𝘂𝗼𝘂𝘀 𝗱𝗲𝗹𝗶𝘃𝗲𝗿𝘆: Jenkins can automate the deployment of applications to various environments, streamlining the release process.
3. 𝗘𝘅𝘁𝗲𝗻𝘀𝗶𝗯𝗹𝗲: With over 1,500 plugins, Jenkins can integrate with a wide variety of tools, including version control systems (like Git), build tools (like Maven), and cloud services.

# Why does this matter? 

Jenkins allows development teams to deliver better software faster, reducing bottlenecks and improving collaboration across teams. 🚀

###  REAL WORLD SCENARIO  ###
Let's consider a real-world scenario where Jenkins is used in a typical software development workflow:

1. **Version Control**: Developers commit their code changes to a version control system like Git.

2. **Continuous Integration**: Jenkins is set up to monitor the version control system for changes. Whenever a new commit is made, Jenkins automatically triggers a build process.

3. **Build**: Jenkins checks out the latest code from the repository and performs a build process. This typically involves tasks such as compiling the code, running unit tests, and generating build artifacts.

4. **Automated Testing**: After the build is successful, Jenkins triggers automated tests. These tests can include unit tests, integration tests, functional tests, and more, depending on the project's requirements.

5. **Code Quality Analysis**: Jenkins can integrate with code analysis tools like SonarQube or Checkstyle to perform static code analysis and generate reports on code quality, coding standards, and potential issues.

6. **Artifact Storage**: Jenkins archives the build artifacts, including compiled binaries, documentation, and other relevant files.

7. **Deployment**: Jenkins can deploy the built artifacts to various environments, such as staging or production servers. This can involve tasks like deploying to application servers, configuring databases, or setting up infrastructure.

8. **Notification and Reporting**: Jenkins sends notifications to relevant stakeholders, such as developers, testers, or project managers, about the build status, test results, and any issues encountered. It can also generate reports and metrics for monitoring and tracking the progress of the software development process.

9. **Continuous Deployment**: Jenkins can be configured to automate the deployment process to production environments based on predefined conditions and approvals. This ensures that code changes are seamlessly delivered to users without manual intervention.

10. **Monitoring and Scaling**: Jenkins can integrate with monitoring and alerting tools to track the performance and health of deployed applications. It can also scale the application infrastructure based on predefined rules or triggers.

11. **Scheduled Jobs**: Jenkins allows the scheduling of jobs for recurring tasks such as backups, database cleanups, or periodic maintenance tasks.

By leveraging Jenkins in this scenario, teams can achieve continuous integration, automated testing, code quality analysis, and streamlined deployment processes. Jenkins helps to automate repetitive tasks, ensure code stability, and improve collaboration among team members. Additionally, it provides visibility into the entire software development lifecycle, enabling efficient management and monitoring of the project.


# AWS EC2 Instance

1. Go to AWS Console
2. Instances(running)
3. Launch instances

<img width="994" alt="215974891-196abfe9-ace0-407b-abd2-adcffe218e3f" src="https://github.com/user-attachments/assets/6b3bab36-28b5-4d89-834f-481693c6a123">

# Install Jenkins.
Pre-Requisites:

Java (JDK)

# Ways To Install Jenkins on linux

--- INSTALL JENKINS ON LINUX METHOD -1 ---

``` shell

sudo apt update -y
sudo apt install openjdk-17-jre -y

curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update -y 
sudo apt-get install jenkins -y

sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins



```
--- INSTALL JENKINS ON LINUX METHOD -2 ---
```shell
sudo apt update -y
sudo apt install openjdk-11-jre -y
sudo wget https://updates.jenkins.io/download/war/2.387.3/jenkins.war
java -jar Jenkins.war  --httpPort=8082


```

𝗡𝗼𝘁𝗲: By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules as show below.

1. EC2 > Instances > Click on
2. In the bottom tabs -> Click on Security
3. Security groups
4. Add inbound traffic rules as shown in the image (you can just allow TCP 8080 as well, in my case, I allowed All traffic).

   <img width="1187" alt="215975712-2fc569cb-9d76-49b4-9345-d8b62187aa22" src="https://github.com/user-attachments/assets/772debf4-7a22-43e1-b94d-41d3467d980b">

# Login to Jenkins using the below URL:
http://:8080 [You can get the ec2-instance-public-ip-address from your AWS EC2 console page]

Note: If you are not interested in allowing All Traffic to your EC2 instance 1. Delete the inbound traffic rule for your instance 2. Edit the inbound traffic rule to only allow custom TCP port 8080

After you login to Jenkins, - Run the command to copy the Jenkins Admin Password - sudo cat /var/lib/jenkins/secrets/initialAdminPassword - Enter the Administrator password

<img width="1291" alt="215959008-3ebca431-1f14-4d81-9f12-6bb232bfbee3" src="https://github.com/user-attachments/assets/80d58996-6b3d-4b9f-bebc-a7e0c88081f7">

# Click on Install suggested plugins

<img width="1291" alt="215959294-047eadef-7e64-4795-bd3b-b1efb0375988" src="https://github.com/user-attachments/assets/a95217ca-296c-426a-b98e-07b0463ef764">

Wait for the Jenkins to Install suggested plugins

<img width="1291" alt="215959398-344b5721-28ec-47a5-8908-b698e435608d" src="https://github.com/user-attachments/assets/ee8acdee-ce41-4e8f-b823-d4976dc2b824">

Create First Admin User or Skip the step [If you want to use this Jenkins instance for future use-cases as well, better to create admin user]

<img width="990" alt="215959757-403246c8-e739-4103-9265-6bdab418013e" src="https://github.com/user-attachments/assets/9d8480a7-5aac-4afc-b630-a7a855b336ec">

Jenkins Installation is Successful. You can now starting using the Jenkins

<img width="990" alt="215961440-3f13f82b-61a2-4117-88bc-0da265a67fa7" src="https://github.com/user-attachments/assets/3e743254-29d2-43d3-818f-d1b198fabd2c">

# Jenkins Guide: Installing Plugins, Global Tool Configuration, Configure System, and Adding Credentials

In this guide, we will walk you through the process of installing plugins, configuring global tools, setting up system configurations, and adding credentials in Jenkins. Let's get started!
# Installing Plugins
1. From the Jenkins dashboard, click on "Manage Jenkins" in the left sidebar.
2. Select "Manage Plugins" to access the plugin installation page.
3. In the "Available" tab, you can browse and search for plugins you want to install.
4. Check the box next to the plugin(s) you want to install.
5. Click on the "Install without restart" button to install the selected plugin(s).
6. Wait for the installation process to complete. You can view the progress on the Jenkins console.
7. Once the installation is finished, you may be prompted to restart Jenkins. If required, click on the "Restart Jenkins when installation is complete and no jobs are running" checkbox and then click "Continue."

# Global Tool Configuration
From the Jenkins dashboard, click on "Manage Jenkins" in the left sidebar.
Select "Global Tool Configuration" to access the tool configuration page.
Scroll down to the section corresponding to the tool you want to configure (e.g., JDK, Git, Maven).
Click on the "Add JDK"/"Add Git"/"Add Maven" button to configure each tool individually.
Provide the necessary details such as name, path, version, etc., depending on the tool you are configuring.

# Configure System
1. From the Jenkins dashboard, click on "Manage Jenkins" in the left sidebar.
2. Select "Configure System" to access the system configuration page.
3. Here, you can modify various system-wide settings and configurations.
4. Review and update the configuration options based on your requirements. Some common configurations include:
5. Jenkins URL: Set the Jenkins URL to access the Jenkins server.
6. System Message: Add a system message to display on the Jenkins dashboard.
7. E-mail Notification: Configure the email settings for Jenkins notifications.
8. Security Settings: Configure security options like access control, user management, and authorization strategies.
9. Click on "Save" to save the system configuration.



# Adding Credentials
1. From the Jenkins dashboard, click on "Credentials" in the left sidebar.
2. Select "System" to access the system credentials page.
3. Click on "Global credentials (unrestricted)" or a specific domain to add credentials.
4. Click on the "Add Credentials" link to add a new credential entry.
5. Choose the credential type from the available options (e.g., Username and Password, SSH Username with Private Key, Secret Text, etc.).
6. Fill in the required fields for the selected credential type, such as username, password, private key, etc.
7. Provide an optional description to help identify the credential entry.
8. Click on "OK" to save the credential entry.
9. Click on "Save" to save the global tool configuration.

That's it! You have now installed plugins, configured global tools, set up system configurations, and added credentials in Jenkins. These configurations will enable you to enhance the capabilities of your Jenkins environment and customize it to meet your specific needs.

🚀 Start automating your software development workflow with Jenkins! 🚀

# Install the Docker Pipeline plugin in Jenkins:

1. Log in to Jenkins.
2. Go to Manage Jenkins > Manage Plugins.
3. In the Available tab, search for "Docker Pipeline".
4. Select the plugin and click the Install button.
5. Restart Jenkins after the plugin is installed.
 Wait for the Jenkins to be restarted.

# Docker Slave Configuration
Run the below command to Install Docker

``` shell

sudo apt update
sudo apt install docker.io

```

# Grant Jenkins user and Ubuntu user permission to docker deamon.

``` shell
sudo su - 
usermod -aG docker jenkins
usermod -aG docker ubuntu
systemctl restart docker

```

Once you are done with the above steps, it is better to restart Jenkins.

``` shell

http://<ec2-instance-public-ip>:8080/restart

```
The docker agent configuration is now successful.

# Jenkins Job Tutorial

In this tutorial, we'll walk you through the process of creating three types of Jenkins jobs: Freestyle, Pipeline, and Multibranch. Each job will have stages for Git checkout, Maven compile, Maven package, and deploying to Tomcat. Let's get started!

# Freestyle Job

1. From the Jenkins dashboard, click on "New Item" to create a new job.
2. Enter a name for the job and select "Freestyle project" as the job type.
3. In the job configuration page, go to the "Source Code Management" section and choose your Git repository. Configure the branch or repository URL as per your requirements.
4. In the "Build" section, click on "Add build step" and select "Execute shell" from the dropdown.
5. In the shell script section, enter the following commands:

``` shell

#!/bin/bash

# Git checkout
git checkout <branch_name>

# Maven compile
mvn compile

# Maven package
mvn package

# Deploy to Tomcat
# Replace 'webapp.war' with your generated WAR file name and adjust the Tomcat server details
cp target/webapp.war /path/to/tomcat/webapps/

```

6. Click on "Save" to save the job configuration.

# Pipeline Job
1. From the Jenkins dashboard, click on "New Item" to create a new job.
2. Enter a name for the job and select "Pipeline" as the job type.
3. In the job configuration page, scroll down to the "Pipeline" section.
4. Choose the "Pipeline script" option and enter the following script:

``` shell

pipeline {
  agent any
  
  tools{
        jdk 'jdk11'
        maven 'maven3'
        }
  
  stages {
    stage('Git Checkout') {
      steps {
        // Git checkout
        git branch: '<branch_name>', url: '<git_repository_url>'
      }
    }
    
    stage('Maven Compile') {
      steps {
        // Maven compile
        sh 'mvn compile'
      }
    }
    
    stage('Maven Package') {
      steps {
        // Maven package
        sh 'mvn package'
      }
    }
    
    stage('Deploy to Tomcat') {
      steps {
        // Deploy to Tomcat
        sh 'cp target/webapp.war /path/to/tomcat/webapps/'
      }
    }
  }
}

```

5. Click on "Save" to save the job configuration.

# Multibranch Job
1. From the Jenkins dashboard, click on "New Item" to create a new job.
2. Enter a name for the job and select "Multibranch Pipeline" as the job type.
3. In the job configuration page, go to the "Branch Sources" section.
4. Configure the source for your Git repository, such as GitHub or Bitbucket, and provide the necessary credentials and repository details.
5. In the "Build Configuration" section, click on "Add build step" and select "Pipeline script" from the dropdown.
6. Enter the same pipeline script mentioned in the Pipeline Job section.
7. Click on "Save" to save the job configuration.
8. 
That's it! You have now created three Jenkins jobs: Freestyle, Pipeline, and Multibranch, with stages for Git checkout, Maven compile, Maven package, and deploying to Tomcat. You can trigger these jobs manually or configure them to run automatically based on your requirements.