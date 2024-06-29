# dereck-mongodb

Automated `CI`/`CD` of `MongoDB` with `Dockerfile` + `docker-compose.yml`.

## security

### remote access

Whitelist IPs so we can connect to the database from our local machine.

```bash
sudo ufw enable
sudo ufw allow from <IP-ADDRESS> to any port 27017
```

### root account and auth

I set up a default root account and required authentication to access the database.

Note that when you pass a password you need to escape certain characters such as `$` becomes `%24`.

```bash
# connect from inside the linode
mongosh mongodb://root:password@localhost:27017/
```

```
# connect from local use connection string in compass
mongodb://admin:password@104.200.17.204:27017/
```

## server

```bash
ssh root@104.200.17.204
```

## persistent data across deleted containers/restarts

I named the volume `dereck-mongo-data`.

```bash
docker volume ls
docker volume inspect dereck-mongo-data
# delete volume
docker volume rm dereck-mongo-data
```
