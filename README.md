
# How to connect to Docker Registry

<p align="center">
<img src="icon.png" width="400" alt="Connect Docker Registry" />
</p>





**A Registry** is a stateless, highly scalable server side application that stores and lets you distribute Docker images.
It holds named Docker images and available in different tagged versions.

## Secure Registry

### Linux

1. ***Get a copy of Certificate authority that signed the registry certificate from Register Server.***

```
Server/IP:10.10.10.10 running Harbor -- /etc/ssl/ca.crt
```

2. ***Save CA certificate to Node running Docker engine***

```
 Server/IP:20.20.20.20 – cp ca.crt /etc/ssl/10.10.10.10.crt
```

3. ***Restart Docker***

```
systemctl restart docker
```
4. ***Login to Registry***

```
docker login 10.10.10.10 ---username foo --password-stdin
```

### Windows
1. ***Get a copy of Certificate authority that signed the registry certificate from Register Server.***

```
Server/IP:10.10.10.10 running Harbor -- /etc/ssl/ca.crt
```

2. ***Add to Windows Global Certificate***

```
Start > “Manage Computer Certificate”.
Right click on “Trusted Root Certification Authorities” > “All tasks” > “import”
Browse to the crt file and press “Next” to complete the wizard
```

3. ***Restart Docker***

```
Right click on “Docker” on System tray > “Restart”
```
4. ***Login to Registry***

```
powerShell> docker login 10.10.10.10 ---username foo --password-stdin
```



## Insecure Registry

### Linux

1. ***Add insecure registry details***

```
/etc/docker/daemon.json
{
  “insecure-registries”: [
    10.10.10.20:5000”
   ]   
}
```

2. ***Restart Docker***

```
systemctl restart docker
```

### Windows

1. ***Add insecure registry details***

```
Right click on “Docker” on System tray > “Settings” > “Docker Engine”
{
  “insecure-registries”: [
    10.10.10.20:5000”
   ]
}
```
2. ***Restart Docker***

```
Right click on “Docker” on System tray > “Restart”
```
