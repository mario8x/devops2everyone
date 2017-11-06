# download and install xvwa victim site

* install xvwa on kali linux by following

```

https://www.vulnhub.com/entry/xtreme-vulnerable-web-application-xvwa-1,209/

source: https://github.com/s4n7h0/xvwa

download:

https://www.vulnhub.com/entry/xtreme-vulnerable-web-application-xvwa-1,209/#download

install xvwa on virtual box:

```

* install directly on kali linux: (preferred)
```
https://github.com/s4n7h0/Script-Bucket/blob/master/Bash/xvwa-setup.sh

- If you got issue about certificates verification failed please follow steps below:

https://stackoverflow.com/questions/21181231/server-certificate-verification-failed-cafile-etc-ssl-certs-ca-certificates-c/21181447#21181447
edit line
https://github.com/s4n7h0/xvwa.git
to
git@github.com:s4n7h0/xvwa.git

then run command line:
./xvwa-setup.sh
Type your sql user/password and /var/www/html

- If you got issue about access denied for user 'root'@'localhost' follow this:
https://stackoverflow.com/questions/28068155/access-denied-for-user-rootlocalhost-using-password-yes-after-new-instal
```

# Attacking techniques

## Profiling

1. Infrastructure profiling

2. Application profiling
