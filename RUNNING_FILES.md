### NEW FRONTPLATE

```sh
Use
npx lig-interactive-generator
```

### SET-UP LOCAL DEV

No frp yet

```sh
1. Search and install homebrew
/usr/bin/ruby -e "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/master/install](https://raw.githubusercontent.com/Homebrew/install/master/install))"
2. brew install node
3. npm i frontplate-cli -g
4. ssh-keygen -t rsa (for git generate ssh key ) just enter
5. pbcopy ~/.ssh/id_rsa.pub or cat ~/.ssh/id_rsa.pub (for reviewing the generated shh key)
6. Then copy the generated ssh key
7. Go to your bitbucket settings
8. Ssh key then add the key you created
9. The you can now use the git clone not the https (more faster)
```
Clone first the frp
```sh
For Wordpress frontplate / frontplate
1. On terminal, frp create wp-belle -g liginc/wordpress-frontplate
2. If you are already in the folder On terminal, frp create ./ -g liginc/wordpress-frontplate
3. On docs, follow readme
4. On terminal, npm install | nom I
5. npm start
```

### DUMPING LOCAL SQL

```sh
bash scripts/mysqldump.sh
```

Remove this part before importing to server
```sh
CREATE DATABASE
USE `wordpress`;
```

### RUNNING LOCAL HTML
```sh
php -S localhost:3000
```

### DOCKER

```sh
docker stop $(docker ps -aq) - stop running containers
docker rm -f $(docker ps -aq) - remove containers
docker container rm cc3f2ff51cab cd20b396a061 - remove containers

`docker rmi <IMAGE-ID>` - clear images
`docker kill <CONTAINER-ID>` - kill current running container
`docker rmi -f $(docker images -a -q)` - shortcut for clear image

`docker system df` - out of disk
`docker system prune -a --volumes` - clean everything
```

### ACCESSING DOCKER CONTAINER

```sh
From test server without `create database`
docker ps
docker exec -it 798a0e17ffe2 bash
cd d
cd docker-entrypoint-initdb.d/
mysql -uroot -ppassword
Exit
mysql -uroot (USER) -ppassword (PASS) wordpress (DB_NAME) < seika-kindergarten.sql (from test server)

either

mysql -uroot -ppassword
mysql -uroot -ppassword wordpress < wordpress.sql

create database
```
