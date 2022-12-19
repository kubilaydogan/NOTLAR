# Jenkins

## **Prerequisite**

- [Install Maven](Install_Maven.md)

- Download Jenkins

    > For Mac: <br> `brew install jenkins-lts`

    > For [Windows](https://www.jenkins.io/download/thank-you-downloading-windows-installer/)

<br>

## **Using Jenkins**

> Start the Jenkins service:<br> `brew services start jenkins-lts`

> After starting the Jenkins service, browse to <br>`http://localhost:8080` <br>and follow the instructions to complete the installation.

<br>

### **Unlock Jenkins**

When you access Jenkins for the first time, you are asked to unlock it using a secret initial admin password. 

<img src="img/unlock.png" width=700></img>

> Enter in Terminal:<br> `pbcopbcopy < /Users/{your_username}/.jenkins/secrets/initialAdminPassword` <br>and paste the password

After you will create the first administrator user.

When done, you will be navigated to dashboard:

<img src="img/dashboard.jpg" width=700></img>

<br><br>

## **Install & Configure Maven Build Tool On Jenkins**

The reason behind integrating Maven with Jenkins is so that we can execute Maven commands through Jenkins as we will majorly use Maven for Java projects. 

Manage Jenkins ➡️ Global Tool Configuration ➡️ Click **Add Maven** ➡️ Uncheck **Install automatically** ➡️ Add a parameter and enter the path. 

<img src="img/mvn.png" width=700></img>

<br>

## **Notes**
> To stop the Jenkins server: <br>`brew services stop jenkins-lts`

> Restart the Jenkins service: <br>`brew services restart jenkins-lts`

>Update the Jenkins version:<br> `brew upgrade jenkins-lts`

<br><br>

----
## **`Create a simple Freestyle Project`**
----
Dashboard ➡️ New Item ➡️ Select **Freestyle Project**

Enter repo url and define branch:
<img src="img/jenkins1.png" width=700></img>

Enter the maven_path parameter you created before and your mvn command to run the tests.

<img src="img/jenkins2.png" width=700></img>

After saving, you can run your tests by clicking the `Build Now` button.

<img src="img/jenkins-build.png" width=700></img>