# 1.Git Work Flow
The project was picked up from the containerization of a microservice from last time using docker. The first step was selecting a good base virtual machine which in my case was ubuntu.22.2 as directed in the instructions.

Vagrant init was the first command ran to add the vagrant file then the following files and folders were created
    - ansible.cfg: Contains the confuguratin files for running of the VM
    - playbook.yml: Contains all instructions that the ansible will follow to achieve automation
    - Hosts file: contains the public key and the name of ypur server
    - Roles: Breaks down major tasks into smaller tasks for better code reuse and also helps in code organization.


# 2. Ansible roles Created 
    - Install docker: This installed docker and all its dependecies
    - Clone repo: This cloned the repo then into a folder ubuntu 
    - create Volume: This created a volume which was to be used by the database that was created
    - createNetwork: This created the network from the three containers could interact
    - databaseConfiguration: This created database from the baseimage mongo assigned a volume and network to it. Port was also assigned to the netwrk
    - backendConfiguration: This created the backend container which was then assigned a network and a volume
    - clientConfiguration: This created the client container which was then assigned a network and a volume

# 3. Testing 
    - The whole setup is started by running vagrant provison or ansible-playbook playbook.yml to execute the application.
    - Log into the VM using vagrant ssh command.
    - Run docker image ls to view whether the containers have been started and are running