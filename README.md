# Sprawozdanie Lab10

# Polecenia użyte do uruchomienia kontenerów
```
docker network create lab10net

docker run -d --name web1 --network lab10net -p 8081:80 -v C:\Users\Varep\Desktop\chmuryLab10\lab10-logs\web1:/var/log/nginx -v C:\Users\Varep\Desktop\chmuryLab10\lab10-html:/usr/share/nginx/html:ro nginx:latest

docker run -d --name web2 --network lab10net -p 8082:80 -v C:\Users\Varep\Desktop\chmuryLab10\lab10-logs\web2:/var/log/nginx -v C:\Users\Varep\Desktop\chmuryLab10\lab10-html:/usr/share/nginx/html:ro nginx:latest

docker run -d --name web3 --network lab10net -p 8083:80 -v C:\Users\Varep\Desktop\chmuryLab10\lab10-logs\web3:/var/log/nginx -v C:\Users\Varep\Desktop\chmuryLab10\lab10-html:/usr/share/nginx/html:ro nginx:latest
```

# Wynik działania
```
2644b7021aad920a74f4bd6fbe3d2523e07675fdb22f4ad77f3bb7b44fc716eb

8738757be1c6fa3de7de1a3c8f88c7707e61d59a4595e4cd673b9ea45bc2c222

2cfc34f024183a11f0b66117a13acb1e7d225789b639ea5d2e622688d97eb412
```

# Sprawdzenie statusu kontenerów

```
docker ps

# Wynik działania:

CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS              PORTS                  NAMES
2cfc34f02418   nginx:latest   "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:8083->80/tcp   web3
8738757be1c6   nginx:latest   "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:8082->80/tcp   web2
2644b7021aad   nginx:latest   "/docker-entrypoint.…"   5 minutes ago        Up 5 minutes        0.0.0.0:8081->80/tcp   web1
```
