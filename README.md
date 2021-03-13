# NGINX SSL Proxy

This image is indented for use in conjunction with the `datameta/certbot-proxy` image.

Example compose usage:

```yaml
reverse-proxy:
  image: "datameta/nginx-ssl-proxy:v1.0.0"
  volumes:
    - etc-le:/etc/letsencrypt      # Persistent volume for certificates
    - www-certbot:/var/www/certbot # Temporary volume for challenge data
  ports:
    - "80:80"
    - "443:443"
  environment:
    NGINX_PROXY_PASS: "http://appserver/" # Hostname of the target application container
    NGINX_HOSTNAME: my.domain.example     # The server_name to use
    NGINX_CLIENT_MAX_BODY_SIZE: 4g        # The maximum request body size to accept
```
