# Installing Jenkins on Red Hat 9

This guide provides step-by-step instructions to install Jenkins on a Red Hat 9-based system using the official Jenkins repository and OpenJDK.


## 🧰 Prerequisites
- A Red Hat 9-based system (or compatible like CentOS Stream/Rocky Linux)
- Sudo/root privileges
- Internet access

## 📦 Step-by-Step Jenkins Installation
### 1. Download and add the Jenkins repository file
```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
```
- This command fetches the Jenkins YUM repository file and places it in the appropriate directory so that yum can find and install Jenkins packages.



### 2. Import the Jenkins GPG key
```bash
rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```
- This imports the GPG key used to verify the Jenkins packages to ensure their authenticity and integrity.


### 3. Update the system
```bash
sudo yum upgrade
```
- This updates all installed packages to the latest versions available in your enabled repositories. It's good practice before installing new software.

### 4. Install OpenJDK (Java 21)
```bash
yum install fontconfig java-21-openjdk
```
- Jenkins requires Java to run. This command installs the required Java runtime (Java 21 in this case) and fontconfig (required for Java GUI rendering, even if unused).


### 5. Install Jenkins
```bash
yum install jenkins
```
- Installs the Jenkins service using the Jenkins YUM repository.




### 6. Start Jenkins service
```bash
systemctl start jenkins
```
- Starts the Jenkins service so it begins running in the background.

### 7. Check Jenkins service status
```bash
systemctl status jenkins
```
- Verifies that the Jenkins service is running properly. You should see "active (running)".

### 8. Verify Jenkins Installation
- Open your web browser and visit:

```cpp
http://<your-server-ip>:8080
http://3.108.42.24:8080
```
This will open the Jenkins dashboard. The first time you access it, Jenkins will prompt you for an administrator password.

### 9. Retrieve the Jenkins initial admin password
```bash
cat /var/lib/jenkins/secrets/initialAdminPassword
```
Copy the password shown in the output and paste it into the Jenkins setup page to unlock the Jenkins dashboard.


## ✅ Jenkins is Now Installed
After entering the password:
- Install suggested plugins
- Create your first admin user
- Start building and managing Jenkins jobs


## 📝 Final Note
Ensure that port 8080 is open in your firewall settings or security group (if using a cloud platform like AWS EC2).

