# NGINX with libModSecurity + ModSecurity-nginx connector + OWASP ModSecurity Core Rule Set (CRS) 

The dockerfile of this container has been copied from the [official nginx repo (alpine-perl variant)](https://github.com/nginxinc/docker-nginx/blob/1.15.3/mainline/alpine-perl/Dockerfile) and has been modified to add [ModSecurity library (v3)](https://github.com/SpiderLabs/ModSecurity/tree/v3/master) + [ModSecurity nginx connector](https://github.com/SpiderLabs/ModSecurity-nginx) + [OWASP ModSecurity Core Rule Set (CRS)](https://github.com/SpiderLabs/owasp-modsecurity-crs)

You can refer to the [official nginx image documentation](https://hub.docker.com/_/nginx/) for instructions on how to use this image.

When you provide your configuration you can enable modsecurity. Please refer to [their wiki](https://github.com/SpiderLabs/ModSecurity/wiki) for documentation.

## Extras

If you're curious to know the difference from this dockerfile and the upstream one:

```bash
diff <(curl -fsL https://github.com/nginxinc/docker-nginx/raw/1.15.3/mainline/alpine-perl/Dockerfile) <(curl -fsL http://github.com/traceflight/docker-nginx-modsecurity/raw/master/Dockerfile)
```
