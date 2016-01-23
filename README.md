Role Name
=========

Installs GoCD (Go Continuous Delivery) https://www.go.cd

Requirements
------------

None

Vagrant
-------
Spin up Environment under Vagrant to test.
````
vagrant up
````

Role Variables
--------------

````
---
# defaults file for ansible-gocd
gocd_repo_key: 'https://bintray.com/user/downloadSubjectPublicKey?username=gocd'
gocd_repo: 'deb http://dl.bintray.com/gocd/gocd-deb/ /'
gocd_server: false  #defines if go-server should be installed. You will want to define this as true only on specific hosts to function as a server
gocd_agent: true  #defines if go-agent should be installed. All hosts require an agent
````

Dependencies
------------

Install required dependencies as below:
````
sudo ansible-galaxy install -r requirements.yml
````

Example Playbook
----------------

#### GitHub
````
---
- name: Install GoCD
  hosts: all
  sudo: true
  vars:
  roles:
    - role: ansible-gocd
  tasks:
````

#### Galaxy
````
---
- name: Install GoCD
  hosts: all
  sudo: true
  vars:
  roles:
    - role: mrlesmithjr.gocd
  tasks:
````

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
