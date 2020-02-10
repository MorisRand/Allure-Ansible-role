# Ansible role to deploy Allure testing report framework in Docker container
[Allure](http://allure.qatools.ru/) is a service for representing results of
test written in different languages and testing frameworks in pleasant web-based view.

This roles does a number of things to deploy such service:
- Sets up a directory where results of tests would be transferred via SFTP.
  The destination directory is **chrooted**, so running the role would make
  neccessary changes to your `/etc/ssh/sshd_config`.
  Special user `allure` would be created to operate transfers, it is nologin,
  can only use chrooted SFTP.
- Install Docker services for Allure. 
The following container is used: https://github.com/fescobar/allure-docker-service
- Sets up a systemd daemon for it.

> __Tested with Ubuntu 18.04__. Pathes to systemd conf folder and to location of
docker-compose maybe different in other distros.
