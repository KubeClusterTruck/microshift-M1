# microshift-M1
Local Microshift Configuration + Examples for Macbook Pro M1
## Raw notes on some setup tweaks to pull together a reusable local environment that survives a Microshift restart
1. Used the following docker command, different that in Getting Started doco, as we want to reuse the local container to preserve the hostname.  If the hostname is not resused, the Microshift config will be fubar'd, as if will try to start all the Kube services using an invalid (previous) hostame:
`docker run -d --name microshift --privileged -v microshift-data:/var/lib -p 6443:6443 -p 8080:80 -p 8443:443 quay.io/microshift/microshift-aio:latest`
2. Now use the docker stop/start commands on the microshift container.  If you want to use a new version of Microshift, you will need to rebuild your config & redeploy any operators or apps.
3. Used the following directions to [setup dnsmasq](https://gist.github.com/ogrrd/5831371). I used ".mshift" to forward local requests to Microshift default router, and don't use the default wildcard domain.
