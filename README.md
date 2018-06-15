# fastbook
This project is inspired by MyPaas developed and mantained by  [D2-SI](http://d2-si.fr/) & [S&B Digital](https://sandbdigital.com/fr/) an Ansible playbook for startups or small companies which want to build a modern and fully automated infrastructure.
The main idea started with similair implementation of MyPaas while having broader automation for different IAAS providers both public or private.

This infrastructure will be composed by :
 - Support of different linux distrubition 
 - [Docker](https://www.docker.com/) Swarm 17.xx
 - A software factory
  - [Gitlab](https://github.com/sameersbn/docker-gitlab)
  - [Jenkins](https://jenkins.io/)
  - [Rundeck](https://github.com/captnbp/docker-rundeck)
 - Monitoring with [ELK](https://www.elasticsearch.com/)
 - Team chat with [Slack](https://slack.com/)
 - Productivity tools 
  - [Nextcloud](https://github.com/Wonderfall/dockerfiles)
  - [Dokuwiki](https://github.com/captnbp/docker-dokuwiki)
 - Automatic encrypted backup with [Duplicity](http://duplicity.nongnu.org/) and specific implementation for each providers
 - Security
  - CIS Benchmark for Centos and Ubuntu if possible (based on https://github.com/grupoversia/cis-ubuntu-ansible)
  - [Let's Encrypt](https://letsencrypt.org/)
  - [OpenLDAP](https://github.com/osixia/docker-openldap)
  - [OpenVPN](https://github.com/kylemanna/docker-openvpn/)
  - [Fail2ban](https://github.com/fail2ban/fail2ban)
  - Log management using ELK
  - Vulnerability scanner with OpenVAS and CoreOS Clair (soon)
 - And more !
 
## Preparation

 1. Create an account on Slack and get a token (`slack.team` and `slack.token`)
 3. Create 2 sets of SSH keys for Gitlab (`jenkins.gitlab_webhook_publickey`, `jenkins.gitlab_webhook_privatekey`) and Jenkins Slave (`jenkins.jenkins_slave_privatekey`)
 4. Create a password for Docker Registry and generate its htpasswd string with http://www.htaccesstools.com/htpasswd-generator/ (`registry.pass` and `registry.htpasswd_pass`)
 8. Create an admin mail account on your domain name (`mail.*`)
 9. Generate many passwords, passphrases, secret keys, encrypting keys with `pwgen 64 20`
 10. Rename `vars.yml-template` to `vars.yml`
 11. Fill every field in `vars.yml` with everything we just generated
 
## Install
 
 1. Create all elements of your cloud project : `ansible-playbook -i ansible_hosts --ask-sudo-pass main.yml`
 2. Create your VMs and install all the tools : `ansible-playbook -i ansible_hosts --ask-sudo-pass deploy.yml`
  

