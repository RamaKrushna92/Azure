# installation of java on Ubuntu
# check if java installed or not on the mechine
java -version

# if it is not installed, than proceed with below

sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version
openjdk version "21.0.3" 2024-04-16
OpenJDK Runtime Environment (build 21.0.3+11-Debian-2)
OpenJDK 64-Bit Server VM (build 21.0.3+11-Debian-2, mixed mode, sharing)

# check for the jenkins installtion status
jenkins --version
# if not above command prints the version, prceed with exicuting the below commands

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

# then verify the jenkins instalation with below command

jenkins --version

# check the status of jenkins, is up and running or not, and port no.

ps -ef | grep jenkins

# after that go to browser and enter the vm ip address and port 8080, but you are not able to access the jenkins, due to 8080 port no.

# by default in Azure vm, 8080 will not be enabled, for that we need to create the port rule for inbound section
# Go to VM and Networking, under Networking go to create port rule, and create with port 8080, than go back to browser and refresh the page, then you will enter into the jenkins dasboard page.

# perform the command to get the key from below
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
# now you will be able to access the jenkins home page, and select the suggest install plugin to get started with jenkins.
