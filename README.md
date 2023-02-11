This repository accompanies my answer to <https://stackoverflow.com/q/75417732/147356>.

## Deploying this example

Run:

```
kubectl apply -k .
```

This will create the `app1` and `app2` namespaces, each running a sample application. It will deploy an Ingress resource in each namespace so that requests to `http://web.example.com/app1` go to app1, and requests to `http://web.example.com/app2` go to app2.

## Testing

```
$ curl -sf -H 'Host: web.example.com' your.ingress.address/app1 | grep Hostname
Hostname: whoami-app1-5dbf5d5bc4-gzmsz
$ curl -sf -H 'Host: web.example.com' your.ingress.address/app2 | grep Hostname
Hostname: whoami-app2-5dbf5d5bc4-pwxb6
```
