## Project Pet Clinic
### VERSION CONTROL STAGE
1. Select repository host - Git
2. Repository strategy single vs multi
3. Branching strategy
   * master
   * dev
   * release
4. User roles and rights
5. User groups
6. Pull Request policy


### BUILD STAGE
1. Local development setup for developers
   * Which IDE?
   * Which build tool? package manager
2. Public/private package dependencies? Module structure
3. Preparing local build scripts
4. CI server installation and configuration
5. Docker registry setup
6. Preparing build agents/env
   * Docker images/AMI(s)
7. CI server build configurtions
   * Pipeline (s)
   * Build scripts


### MSP1 -- Prepare Development Server Manually on EC2 Instance
- Amazon Linux 2
- t2.medium
- Key:Name, Value: Petclinic Dev Server
- Ports: all
- Keypair
- User-data:
```bash
    ### Creating an environment for the Developer manually, we will automate everything later on
    # update os
    sudo yum update -y
    #set hostname as petclinic-dev-server
    sudo hostnamectl set-hostname petclinic-dev-server
    # install docker
    sudo amazon-linux-extras install docker -y
    sudo systemctl start docker
    sudo systemctl enable docker
    #add ec2 user to the group
    sudo usermod -aG docker ec2-user
    sudo newgrp docker
    # see the info of docker
    docker info 
    # install docker compose
    sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" \
-o /usr/local/bin/docker-compose
    # check the folder for the dowloaded docker compose file
    ls /usr/local/bin | grep docker
    # change permission to executable for docker compose file
    sudo chmod +x /usr/local/bin/docker-compose
    # install JDK 11
    sudo yum install java-11-amazon-corretto -y
    java --version
    # install Git
    sudo yum install git -y

```
### MSP-2-1 
- Fork and clone the Petclinic app from the Clarusway repository Petclinic Microservices Application
- Rename `microservices-ci-cd-pipeline-with-petclinic-app`
- Clone the forked repo from your Github repo on developement server
```bash
git clone https://github.com/qhn74382/microservices-ci-cd-pipeline-with-petclinic-app.git
```
- Prepare base branches namely `master`, `dev`, `release` for DevOps cycle.
  - Create `dev` base branch
  ```bash

  ```
  - Create `release` base branch.
  ```bash

  ```
### UNIT TEST



### DEPLOY
DEPLOYMENT PREP:
1. Setup docker registry
2. Setup artifactory server (Nexus, JFrog)
3. Prepare provisioning (Cloudformation, Terraform) templates for QA, staging infrastructure
4. Docker orchestrator setup (Swarm or Kubernetes)

### AUTO TEST
1. Implementation of test suites (FT, UAT, etc.)(Eng)
2. Update project

### DEPLOY TO PRODUCTION
1. Create production env docker deployment scripts
2. Create 


### MEASURE = VALIDATE
1. Setup Prometheus

Resource:
PetClinic
http://ec2-3-236-111-151.compute-1.amazonaws.com:8080

Maven 5 mins
https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html

Maven Build Cycle
https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html