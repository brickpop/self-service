# Self Service
Docker environment to provide common services for one's server

## Get started

```sh
# CLONE
git clone https://github.com/ledfusion/self-service.git
cd self-service

# DEFINE YOUR CONTACT EMAIL
CONTACT_EMAIL="my-user@my-email.com"
sed -i s/user@email.com/${CONTACT_EMAIL}/g ./init-letsencrypt.sh

# DEFINE YOUR DOMAIN
MY_DOMAIN="my-top-level-domain.com"
grep -R example.com . | cut -d':' -f1 | uniq | while read f ; do sed -i s/example.com/${MY_DOMAIN}/g $f ; done

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