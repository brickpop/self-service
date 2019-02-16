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

## Wiki.js

Login with $WIKI_USER_EMAIL and password `admin123`. Change it when done.
