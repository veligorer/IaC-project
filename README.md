# infrastructure as code with simple kubernetes deployment

In this project demonstrace infrastructure as code principles with simple kubernetes deployment . we have 3 servers(Server 1, Server 2, Server 3). Server 1 for kubernetes master Server 2  for kubernetes worker and Server 3 is common server for jenkins and private docker registry

### Prerequisite
* git
* virtualbox
* vagrant 

### Steps

#### Clone source code from git
```
git clone https://github.com/veligorer/IaC-project.git
```
#### Change directory
```
cd IaC-project
```

#### Create empty ca.crt file
```
touch setup-playbook/files/ca.crt
```

#### Create and provision servers with vagrant 
```
vagrant up
```

#### Check servers up and running 
```
vagrant status 

#Expected output
Current machine states:

k8s-master                running (virtualbox)
k8s-worker1               running (virtualbox)
common                    running (virtualbox)

```

#### Test application up and running with your browser 
```
#Enter this url in your browser
http://192.168.50.11:30000/
```

#### There are screenshot of project
```
cd screenshot
ls 
# Expected output
ansible-playbook-output.png       docker-pets-job-logs.png      jenkins-dashboard.png  vagrant-status.png
docker-pet-job-configuration.png  jenkinsanddockerregistry.png  kubernetes-output.png
```

#### Clean your setup with vagrant 
```
# Enter yes for deleting your servers
vagrant destroy
```
