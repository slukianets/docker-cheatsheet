Tasks
===
### 1. sha256 sum
```
sha256: b643c0b5f0f35c33f28e886f7ac9e359ff045b3ae0f51bb62448a2265b186336  docker
```

### 2. ubuntu
```
sha256: 
865469589c2453b1da95547235c029d05b8d81782058b265c1300bae641366dc  /etc/debian_version
ed46d9be2771ad779b35b358d708140cc8942e36ed07806648123155b41fa665  /etc/os-release
```

### 3. centos
```
find / -type f -name "sha256sum"
/usr/bin/sha256sum

sha256: 59297533a5f227751cce6fdd6ad471f3f3631deb600d6821f02930f1e92c26fd  /usr/bin/sha256sum
```

### 4. alpine
```
docker run -it alpine cat /etc/passwd | wc -l
28
```

### 5. busybox
```
docker run -it busybox df -h / | awk '/overlay/ {print $2}'
8.0G
```

### 6. hello-world
```
sha256: 1249d4488a1b6e09c2f054f7015dcd003dd60f6909ae2bf888f91da6ac265a52 
```


### 7. apache
```
root      4241  0.1 10.1 791680 102432 ?       Ssl  08:16   0:13 /usr/bin/dockerd --default-ulimit nofile=1024:4096
root      4353  0.1  2.6 648584 27076 ?        Ssl  08:16   0:13  \_ docker-containerd --config /var/run/docker/containerd/containerd.toml
root     12165  0.0  0.3   7384  3880 ?        Sl   10:43   0:00      \_ docker-containerd-shim -namespace moby -workdir /var/lib/docker/containerd/daemon/io.containerd.runtime.v1.linux/moby/d4f2f319c592bfe1311a44a7972c075cc4b36b39b564
root     12209  0.1  0.4   6088  4548 ?        Ss   10:43   0:00          \_ httpd -DFOREGROUND
bin      12253  0.0  0.3 752004  3412 ?        Sl   10:43   0:00              \_ httpd -DFOREGROUND
bin      12254  0.0  0.3 752004  3412 ?        Sl   10:43   0:00              \_ httpd -DFOREGROUND
bin      12255  0.0  0.3 752004  3412 ?        Sl   10:43   0:00              \_ httpd -DFOREGROUND
...........
Processing triggers for libc-bin (2.28-10) ...
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.4   6088  4556 ?        Ss   10:52   0:00 httpd -DFOREGROUND
daemon       7  0.0  0.3 752004  3504 ?        Sl   10:52   0:00 httpd -DFOREGROUND
daemon       8  0.0  0.3 752004  3500 ?        Sl   10:52   0:00 httpd -DFOREGROUND
daemon       9  0.0  0.3 752004  3504 ?        Sl   10:52   0:00 httpd -DFOREGROUND
root       101  0.1  0.3   3868  3124 pts/0    Ss   10:54   0:00 /bin/bash
root       417  0.0  0.2   7640  2744 pts/0    R+   10:54   0:00 ps aux

```

### 8. compile c program
```
ubuntu sha256: 751613838cb1bdbe778ca405d74e2911dd0ab4a0d0584ac740be30906694e38c  /hello
centos sha256: 90635dcf93c75a7185bc85c4ab22f598e422fc1272ecde70fbc792edf2df59c5  /hello
```
