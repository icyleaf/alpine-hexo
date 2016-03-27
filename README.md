# Minimal Hexo Docker Images (176 MB)

Inspired by [simplyintricate/hexo](https://hub.docker.com/r/simplyintricate/hexo/) but build with [Alpine](http://www.alpinelinux.org/) Linux.

## Hexo

> A fast, simple & powerful blog framework, powered by Node.js.

## Support

- [nginx-proxy](https://github.com/jwilder/nginx-proxy)
- [let's encrypt iti](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion)

## Example

### Start Hexo

```bash
$ [sudo] docker run --name hexo -it \
     -v /path/to/source:/DATA/source \
     -p 80:80 \
     icyleafcn/alpine-hexo
```

### Nginx Proxy

To run nginx-proxy first:

```bash
$ [sudo] docker run -d -p 80:80 -v /var/run/docker.sock:/tmp/docker.sock:ro jwilder/nginx-proxy
```

Then append env `-e VIRTUAL_HOST=domain.com`:

```bash
$ [sudo] docker run --name hexo -it \
     -e VIRTUAL_HOST=domain.com \
     -v /path/to/source:/DATA/source \
     -p 80:80 \
     icyleafcn/alpine-hexo
```

### Let's Encrypt it

Follow the tutorial first [here](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion#usage), then repeat below command:

```bash
$ [sudo] docker run --name hexo -it \
     -e VIRTUAL_HOST=domain.com \
     -e LETSENCRYPT_HOST=domain.com,www.domain.com \
     -e LETSENCRYPT_EMAIL=your@email.com \
     -v /path/to/source:/DATA/source \
     -p 80:80 \
     icyleafcn/alpine-hexo
```
