# getflat
This script is meant for quick & easy docker, docker-compose, and flat install via:
>curl http://host.wednus.com/getflat | sh

Other than flat, it will basically executing the following script and commands:
```
curl -sSL https://get.docker.com | sh
```
```
sudo apt-get install python-setuptools
sudo easy_install -U pip
sudo pip install docker-compose
```
If you already have docker and docker-compose running, please use '[onlyflat](https://github.com/pipcc/getflat/blob/master/onlyflat)' script instead.

Not sure? You can check using:
```
docker version
```
For docker-compose:
```
docker-compose version
```
# onlyflat
This script is meant for OS with docker installed already to add flat-only via:
>curl http://host.wednus.com/onlyflat | sh
This script will add the following configuration to docker-compose.yaml in $HOME directory:
```
flat:
  container_name: flat
  image: flab/flat
  volumes:
    - flat-data:/data
    - /var/run/docker.sock:/var/run/docker.sock
  ports:
    - 9000:9000
  restart: always
```
To prevent noob mistake, it will backup existing docker-compse.yaml to docker-compose_old_$(date +'%m%d%y').yaml before creating new one having itself as the only body content.

If you feel comfortable editing docker-compose.yaml, you don't need this script, Instead you can add this block somewhere in the file (keep the indention) and do:
```
docker-compose up -d
```
Then visit http://[IP of SBC]:9000 for start using flat.
