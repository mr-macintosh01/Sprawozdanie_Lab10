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

# Potwierdzenie działania serwerów

```
http://localhost:8081
```
![image](https://github.com/mr-macintosh01/Sprawozdanie_Lab10/assets/65767905/1417fd5e-214b-4164-9082-c298b2905ccf)
```
http://localhost:8082
```
![image](https://github.com/mr-macintosh01/Sprawozdanie_Lab10/assets/65767905/208063a8-9c8c-4c4d-9e47-ad52358296c9)
```
http://localhost:8083
```
![image](https://github.com/mr-macintosh01/Sprawozdanie_Lab10/assets/65767905/d77fe91e-70f7-478f-8db9-c90b0caf212f)

# Dostęp do logów serwerów

Logi serwerów są zapisywane w katalogach lab10-logs/web1, lab10-logs/web2 i lab10-logs/web3 na moim systemie hosta. Mogę uzyskać do nich dostęp za pomocą dowolnego edytora tekstu lub przeglądarki plików. Na przykład, w systemie Windows, mogę otworzyć je za pomocą Notatnika lub dowolnego innego edytora tekstu.

To potwierdza, że wszystkie trzy serwery poprawnie wyświetlają stronę HTML, a logi serwerów zostały poprawnie zapisane i są dostępne na moim systemie hosta.

Przykłady:

```
lab10-logs\web1\access.log

172.18.0.1 - - [26/May/2024:16:49:49 +0000] "GET / HTTP/1.1" 200 181 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36" "-"
172.18.0.1 - - [26/May/2024:16:50:24 +0000] "GET / HTTP/1.1" 200 172 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36" "-"

lab10-logs\web1\error.log

2024/05/26 16:49:45 [notice] 1#1: using the "epoll" event method
2024/05/26 16:49:45 [notice] 1#1: nginx/1.25.4
2024/05/26 16:49:45 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14) 
2024/05/26 16:49:45 [notice] 1#1: OS: Linux 5.10.102.1-microsoft-standard-WSL2
2024/05/26 16:49:45 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2024/05/26 16:49:45 [notice] 1#1: start worker processes
2024/05/26 16:49:45 [notice] 1#1: start worker process 29
2024/05/26 16:49:45 [notice] 1#1: start worker process 30
2024/05/26 16:49:45 [notice] 1#1: start worker process 31
2024/05/26 16:49:45 [notice] 1#1: start worker process 32
```
