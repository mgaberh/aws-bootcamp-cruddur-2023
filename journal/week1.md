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
I used command to run docker using env.
export BACKEND_URL="*".
export FRONTEND_URL="*".
docker run --rm -p 4567:4567 -it -e FRONTEND_URL='*' -e BACKEND_URL='*' backend-flask.

## Insall dynamoDB. 
### create new table:( for local dynamoDB you should add --endpoint-url http://localhost:8000 \ for all command ).

#### aws dynamodb create-table \
    --endpoint-url http://localhost:8000 \
    --table-name Music \
    --attribute-definitions \
        AttributeName=Artist,AttributeType=S \
        AttributeName=SongTitle,AttributeType=S \
    --key-schema AttributeName=Artist,KeyType=HASH AttributeName=SongTitle,KeyType=RANGE \
    --provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1 \
    --table-class STANDARD

#### List Tables:
aws dynamodb list-tables --endpoint-url http://localhost:8000
    
#### add 2 item in table:
aws dynamodb put-item \
    --endpoint-url http://localhost:8000 \
    --table-name Music \
    --item \
        '{"Artist": {"S": "No One You Know"}, "SongTitle": {"S": "Call Me Today"}, "AlbumTitle": {"S": "Somewhat Famous"}}' \
    --return-consumed-capacity TOTAL

aws dynamodb put-item \
    --endpoint-url http://localhost:8000 \
    --table-name Music \
    --item '{
        "Artist": {"S": "Acme Band"},
        "SongTitle": {"S": "Happy Day"},
        "AlbumTitle": {"S": "Songs About Life"} }' \
    --return-consumed-capacity TOTAL

#### Get record:
aws dynamodb scan --table-name Music --query "Items" --endpoint-url http://localhost:8000.

## Install postgree sql database.
### install the postgres client.

name: postgres
    init: |
      curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc|sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/postgresql.gpg
      echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" |sudo tee  /etc/apt/sources.list.d/pgdg.list
      sudo apt update
      sudo apt install -y postgresql-client-13 libpq-dev.

to check postgresql database:.
psql -U postgres --host localhost ( U: user ).
use \l, \d, \t, \dl, \q(to quit) command

