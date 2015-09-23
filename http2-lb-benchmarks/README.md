# http/2 loadbalancer benchmarks


# Running

**nginx**

```
docker build -t http2-nginx ./nginx
docker run -p 80:80 -p 443:443 -d --name http2-nginx deviavir/http2-nginx
```

**caddy**

```
docker build -t http2-caddy ./caddy
docker run -d -p 80:2015 -p 443:2378 --name http2-caddy http2-caddy
```


# Testing

**HTTP/2 and SPDY indicator**
https://chrome.google.com/webstore/detail/http2-and-spdy-indicator/mpbpobfflnpcgagjijhmgnchggcjblin/related?hl=en

# Loadtests

**h2load**
https://nghttp2.org/documentation/h2load-howto.html