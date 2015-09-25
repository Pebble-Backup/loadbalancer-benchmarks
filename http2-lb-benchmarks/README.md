# http/2 loadbalancer benchmarks

### Results

Nginx blowing away the competition.

**nginx**

```
finished in 2.56s, 3903.26 req/s, 1.90MB/s
requests: 10000 total, 10000 started, 10000 done, 10000 succeeded, 0 failed, 0 errored, 0 timeout
status codes: 10000 2xx, 0 3xx, 0 4xx, 0 5xx
traffic: 5104900 bytes total, 1340000 bytes headers, 3580000 bytes data
                     min         max         mean         sd        +/- sd
time for request:      253us     54.75ms     26.74ms      6.70ms    83.33%
time for connect:    15.35ms       2.44s       1.25s    725.13ms    59.00%
time to 1st byte:    19.74ms       2.46s       1.27s    722.96ms    59.00%
```

**caddy**

```
finished in 5.05s, 1978.41 req/s, 739.70KB/s
requests: 10000 total, 10000 started, 10000 done, 10000 succeeded, 0 failed, 0 errored, 0 timeout
status codes: 10000 2xx, 0 3xx, 0 4xx, 0 5xx
traffic: 3828600 bytes total, 65600 bytes headers, 3580000 bytes data
                     min         max         mean         sd        +/- sd
time for request:    12.58ms       1.96s    347.75ms    320.94ms    86.30%
time for connect:   511.08ms       1.00s    713.90ms    129.38ms    56.00%
time to 1st byte:   816.89ms       2.57s       1.41s    406.48ms    71.00%
```


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

```
brew install nghttp2 # if not installed already
h2load -n100000 -c100 -m10 https://192.168.99.100
```
