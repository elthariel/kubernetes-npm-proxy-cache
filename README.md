# kubernetes-npm-proxy-cache

Make `npm install` much faster on your kubernetes deployment, by
deploying a small internal proxy cache for your deployment.

This has been hacked together to make our Jenkins build faster.

## How to use it

First, deploy the proxy cache on your kubernetes cluster:

``` shellsession
$> kubectl apply -f https://github.com/elthariel/kubernetes-npm-proxy-cache/raw/master/npm-proxy-cache.yml
deployment "npm-proxy-cache-deployment" created
service "npm-proxy-cache-service" created
```

Then, anywhere in your Kubernetes cluster:

``` shellsession
$> npm config set proxy http://npm-proxy-cache-service
$> npm config set https-proxy http://npm-proxy-cache-service
$> npm config set strict-ssl false
$> npm install
```
