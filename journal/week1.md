# Week 1 — App Containerization

I decided to run containers on my Linux local machine

after many chalenges I changed my mind as i faced more error reagrding versions and environment in local system
so I decided to work in gitpod

## prepare python environment
I installed Python extinsion on VSCode
Note : we can add dockerfile using command-pallite command ( Docke:Add Docker Files to Workspace )

I prepared python environment by Install python version 3.10.9 using url 
How to Install and Use Pyenv in Ubuntu?
https://itslinuxfoss.com/install-use-pyenv-ubuntu/
then 
( https://github.com/omenking/aws-bootcamp-cruddur-2023/blob/week-1/backend-flask/README.md)

I installed Python3-flask using sudo apt install python3-flask

I installed python3 pip using command ( sudo apt install python3-pip ) in order to install Flask_Cors liberary
I installed Flask-Cors using command ( pip3 install Flask-Cors )

I confirmed the port is open in ubuntu
to dealing with ports and firewall check this url 
https://linuxconfig.org/ubuntu-20-04-open-http-port-80-and-https-port-443-with-ufw
How To Configure Firewall with UFW on Ubuntu 20.04 LTS
https://www.cyberciti.biz/faq/how-to-configure-firewall-with-ufw-on-ubuntu-20-04-lts/

## prepare NodeJS environment
I installed npm for Nodejs

## run docker
I used command to run docker using env
export BACKEND_URL="*"
export FRONTEND_URL="*"
docker run --rm -p 4567:4567 -it -e FRONTEND_URL='*' -e BACKEND_URL='*' backend-flask
