# Master-DevOps

# Small Description
I deploy a GoLang and ReactJS basic application with a back-end and front-end service which uses containers for each and publish it to github.com repositry (You can use your own).

Then I create a docker-compose file where these containers can be served together.

Then I do container orchestration using docker-swarm and kubernetes.

I use Ansible Scripts / Terraform for making clusters.

Once it done i create a Jenkins machine and create a pipeline to do all the above steps automatically on every code push on master branch.


#Full Guide To Setup

1. sudo snap install terraform
or you may get help from there to install terraform
https://askubuntu.com/questions/983351/how-to-install-terraform-in-ubuntu
-----------------------------------------------------------------------------
2. Install ansible
sudo apt install python
sudo apt install python-pip
pip install boto boto3 ansible
----------------------------------------------------------------------------------------------------------------
3. run command: "terraform init" or "sudo terraform init"
   (to initialize the terraform)
----------------------------------------------------------------------------------------------------------------
4. cat ~/.ssh/id_rsa.pub
   (copy the key)
   (generate ssh keygen first if you have not)
----------------------------------------------------------------------------------------------------------------
5. nano main.tf
   (paste the copied key in this file)
   (also change the instance details as required)

(if you want to login with .pem then go to provider.tf and uncomment the pem file command (you will find there)
(you can also provide your security group there : vpc_security_group_ids=["default"]

----------------------------------------------------------------------------------------------------------------
6. create IAM user at AWS with Programmatic and administrative rights, get the access and secret key
----------------------------------------------------------------------------------------------------------------
7. paste those keys in provider.tf
----------------------------------------------------------------------------------------------------------------
8. run command "terraform apply"
   (this will create instances and the keypair at your AWS)
----------------------------------------------------------------------------------------------------------------
9. enter "yes" and go to aws page of running instances to copy the public ip of instances
----------------------------------------------------------------------------------------------------------------
10. Paste it in hosts file with "nano hosts"
    (you can also find ways that it gets the public IP in hosts file when instance are created)
----------------------------------------------------------------------------------------------------------------
11. run the command:
    ansible-playbook -i hosts deployme.yml

(if you get the persmission error.. check your inbound settings at default security group on AWS:
somehow my groupid was entered in the IP section, if you face this issue kindly paste this 0.0.0.0/0
just one time and it wil be fixed permanently)
----------------------------------------------------------------------------------------------------------------
12. wait for the deployment and check by going to your host address, your server should be up
----------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------
"terraform destroy" to destroy all instances and keypair
----------------------------------------------------------------------------------------------------------------

Notes:

- all required yml files is imported in deployme.yml
  

- this is our test project, we cloned from githut repo. 

- run: nano commands.yml and replace your own github repo there
 (you can also import your jenkins configurations from git in commands.yml file)
 (also change the folder location on commands2.yml)

- please go through all yml files to further understand the process

- these are unmanaged yml files, created for this particular project. You can make your own ymls by taking refernce from it and internet. 

BEST REGARDS

contact me if you face any difficulty
and please contribute to improve this work and suggest necessary changes.


