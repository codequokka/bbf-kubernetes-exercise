# 1.2.6
```console
❯ docker run --rm --detach --publish 8080:80 --name web nginx:1.25.3
Unable to find image 'nginx:1.25.3' locally
1.25.3: Pulling from library/nginx
e1caac4eb9d2: Pull complete
504c1e01744e: Pull complete
a1330b43d726: Pull complete
5e8995dba715: Pull complete
d5181593591e: Pull complete
74a4f808141d: Pull complete
330fd09f4306: Pull complete
Digest: sha256:c7a6ad68be85142c7fe1089e48faa1e7c7166a194caa9180ddea66345876b9d2
Status: Downloaded newer image for nginx:1.25.3
3e101d224b90987cbf006e64c6dfa1d5e570a9c65c35572408a4218e88784097

❯ curl localhost:8080
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

# 1.2.9
```console
❯ cd chapter-01/custom-nginx

❯ docker build . --tag nginx-custom:1.0.0
[+] Building 1.3s (7/7) FINISHED                                                              docker:default
 => [internal] load build definition from Dockerfile                                                    0.1s
 => => transferring dockerfile: 152B                                                                    0.0s
 => [internal] load metadata for docker.io/library/nginx:1.25.3                                         0.0s
 => [internal] load .dockerignore                                                                       0.1s
 => => transferring context: 2B                                                                         0.0s
 => [internal] load build context                                                                       0.2s
 => => transferring context: 118B                                                                       0.0s
 => [1/2] FROM docker.io/library/nginx:1.25.3                                                           0.5s
 => [2/2] COPY index.html /usr/share/nginx/html                                                         0.1s
 => exporting to image                                                                                  0.2s
 => => exporting layers                                                                                 0.1s
 => => writing image sha256:d2127e19555518d551029dc4580bf9a862c2de96e9a3020fa29ee2c574e23615            0.0s
 => => naming to docker.io/library/nginx-custom:1.0.0

❯ docker images
REPOSITORY        TAG       IMAGE ID       CREATED          SIZE
nginx-custom      1.0.0     d2127e195555   49 seconds ago   187MB
nginx             1.25.3    247f7abff9f7   14 months ago    187MB
```

# 1.2.10
```console
❯ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                  NAMES
3e101d224b90   nginx:1.25.3   "/docker-entrypoint.…"   30 minutes ago   Up 30 minutes   0.0.0.0:8080->80/tcp   web

❯ docker stop 3e101d224b90
3e101d224b90

❯ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

❯ docker run --rm --detach --publish 8080:80 --name web nginx-custom:1.0.0
8cf82c8eabbe25d9cfcdda410d7bf4d3f41a1913f5fc5f1f11b23bc4aa439d8a

❯ curl localhost:8080
<h1>Hello World!</h1>

❯ docker stop web
web

❯ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

# 1.3
```console
❯ cd chapter-01/hello-server

❯ docker build . --tag hello-server:1.0
<omit>

❯ docker images hello-server
REPOSITORY     TAG       IMAGE ID       CREATED         SIZE
hello-server   1.0       0dba0c365edf   2 minutes ago   6.72MB

❯ docker run --rm --detach --publish 8080:8080 --name hello-server hello-server:1.0
de3fcfdcb04d10ae4e0ed7aa9ed3ccba1c3a0e3bd94ebe2f5582f9adbbce6e8e

❯ curl localhost:8080
Hello, world!%

❯ docker stop hello-server
hello-server

❯ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
