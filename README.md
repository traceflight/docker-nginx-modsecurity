# Nginx with WAF

在[官方ngxin Dockerfile](https://github.com/traceflight/nginx-with-waf/raw/master/Dockerfile)的基础上，增加[ModSecurity V3版本](https://github.com/SpiderLabs/ModSecurity/tree/v3/master)作为WAF。

## 使用方法

### 下载镜像

```bash
docker pull traceflight/nginx-with-waf
```

### 运行

```bash
docker run -d -v /path/to/conf/:/etc/nginx/conf.d/ \
              -v /path/to/log/:/var/log/nginx/ \
              -p 80:80 -p 443:443 \
              traceflight/nginx-with-waf
```

或使用docker-compose：

```yaml
version: '3'
services:
 nginx:
    image: traceflight/nginx-with-waf
    restart: always
    volumes:
      - /path/to/conf/:/etc/nginx/conf.d/
      - /path/to/log/:/var/log/nginx/
    ports:
      - "80:80"
      - "443:443"
```

### Waf配置

默认ModSecurity为开启状态，其使用的owasp-modsecurity-crs规则集有可能会阻断正常的应用数据，如需要关掉ModSecurity,则需要在网站的配置中增加如下语句：

```
modsecurity off;
```

## 依赖项目

* [Nginx](https://github.com/nginxinc/docker-nginx)
* [ModSecurity](https://github.com/SpiderLabs/ModSecurity)
* [ModSecurity nginx connector](https://github.com/SpiderLabs/ModSecurity-nginx)
* [owasp-modsecurity-crs](https://github.com/SpiderLabs/owasp-modsecurity-crs)

## 与官方Dockerfile的区别

可通过如下命令查看当前版本与Nginx官方Dockerfile的区别：

```bash
diff <(curl -fsL https://github.com/nginxinc/docker-nginx/raw/1.15.12/mainline/alpine-perl/Dockerfile) <(curl -fsL https://github.com/traceflight/nginx-with-waf/raw/1.15.12/Dockerfile)
```

# NGINX with libModSecurity + ModSecurity-nginx connector + OWASP ModSecurity Core Rule Set (CRS) 

The dockerfile of this container has been copied from the [official nginx repo (alpine-perl variant)](https://github.com/nginxinc/docker-nginx/blob/1.15.3/mainline/alpine-perl/Dockerfile) and has been modified to add [ModSecurity library (v3)](https://github.com/SpiderLabs/ModSecurity/tree/v3/master) + [ModSecurity nginx connector](https://github.com/SpiderLabs/ModSecurity-nginx) + [OWASP ModSecurity Core Rule Set (CRS)](https://github.com/SpiderLabs/owasp-modsecurity-crs)

You can refer to the [official nginx image documentation](https://hub.docker.com/_/nginx/) for instructions on how to use this image.

When you provide your configuration you can enable modsecurity. Please refer to [their wiki](https://github.com/SpiderLabs/ModSecurity/wiki) for documentation.

## Extras

If you're curious to know the difference from this dockerfile and the upstream one:

```bash
diff <(curl -fsL https://github.com/traceflight/nginx-with-waf/raw/master/Dockerfile) <(curl -fsL https://github.com/traceflight/nginx-with-waf/raw/1.15.12/Dockerfile)
```
