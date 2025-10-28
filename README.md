# 🧰 Jenkins Installation on AWS EC2 Instance

## 🟣 Step 1: Launch an AWS EC2 Instance

1. Go to the **AWS Console**  
2. Launch a new **EC2 instance**  
3. Choose your preferred **AMI** (e.g., Ubuntu)  
4. In the **Security Group**, add an **Inbound Rule** to allow:  
   - **Type:** All Traffic  
   - **Source:** 0.0.0.0/0  
5. Connect the instance to any terminal  

---

## 🟣 Step 2: Install Jenkins on Ubuntu

### ⚙️ Pre-requisites  
- Java (JDK)

### 🟢 Step 2.1: Install Java  
Run the following commands:
```bash
sudo su -
apt update -y
apt install openjdk-17-jre-headless -y
```
### 🟢 Step 2.2: Verify Java Installation
```bash
java --version
```

### 🟣 Step 3: Install Jenkins

Add the Jenkins repository key and source list:
```bash 
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
```
📝 Note:
The above commands are for Ubuntu AMI.
For Amazon Linux or RHEL/CentOS, commands will differ slightly.
Refer to the official Jenkins installation guide for other OS types.

### Update and install Jenkins:
```bash
apt update
apt install jenkins -y
```

### 🟣 Step 4: Verify Jenkins Service
```bash
systemctl status jenkins
```

### 🟣 Step 5: Access Jenkins
```bash
Open the following URL in your browser:

http://<your-ec2-public-ip>:8080
```

### 🟣 Step 6: Get Administrator Password
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword


Enter the above password in Jenkins login.
```

### 🟣 Step 7: Complete Setup

Click Install suggested plugins

Wait for installation to complete

Create your first admin user (or skip)

🎉 Jenkins installation is successful!

