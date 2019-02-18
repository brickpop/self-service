# Self Service
Docker environment to provide common services for one's server

## Get started

```sh
# CLONE
git clone https://github.com/ledfusion/self-service.git
cd self-service

# DEFINE YOUR CONTACT EMAIL
./taskfile customize contact "john@smith.com"

# DEFINE YOUR WIKI USER EMAIL
./taskfile customize wiki-email "john@smith.com"

# DEFINE YOUR DOMAIN
./taskfile customize domain "my-top-level-domain.com"

# SET UP DUMMY CERTIFICATES, START AND GENERATE VALID CERTIFICATES
./init-letsencrypt.sh

# READY!
docker-compose ps
```

Now you have:

* http://my-top-level-domain.com/
* http://www.my-top-level-domain.com/
* https://my-top-level-domain.com/
* https://www.my-top-level-domain.com/
* http://wiki.my-top-level-domain.com/
* https://wiki.my-top-level-domain.com/

## Docker registry

Run `./taskfile htpasswd` to generate a password for the Docker Registry.

Log in to your registry from your local computer:

```
docker login -u=docker -p=<PASSWORD> registry.example.com
```

Tag and push an image:

```
docker tag ubuntu registry.example.com/test
docker push registry.example.com/test
docker pull registry.example.com/test
```

From within the server
```
docker login -u=docker -p=<PASSWORD> localhost:5000
docker pull localhost:5000/test
```

## Wiki.js

Login with your wiki user email and password `admin123`. Change it right after.

## Cleanup

- You can clean unused volumes, containers, images and networks with `./taskfile clean`
- You can get some space back from the Docker Registry by running `./taskfile clean registry`

## TODO

- [ ] Make `taskfile` resilient to changes to its own search/replace tokens
- [x] Docker registry
- [ ] Cryptpad
- [ ] Backup system
