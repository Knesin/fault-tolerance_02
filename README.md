# Домашнее задание к занятию 2 «Кластеризация и балансировка нагрузки» - Клочек Максим

### Задание 1
- Запустите два simple python сервера на своей виртуальной машине на разных портах
- Установите и настройте HAProxy, воспользуйтесь материалами к лекции по [ссылке](https://github.com/netology-code/sflt-homeworks/tree/main/2)
- Настройте балансировку Round-robin на 4 уровне.
- На проверку направьте конфигурационный файл haproxy, скриншоты, где видно перенаправление запросов на разные серверы при обращении к HAProxy.

---
```bash
cd src/http1
python3 -m http.server 8888
cd src/http2
python3 -m http.server 9999
sudo apt update
sudo apt install haproxy 
sudo nano /etc/haproxy/haproxy.cfg
sudo systemctl reload haproxy.service 
curl http://localhost:8080
```

[haproxy.cfg](configs/task1/haproxy.cfg) переместить в `/etc/haproxy/haproxy.cfg`

Результат

![Консоль](img/task1_1.png)
![Статистика](img/task1_2.png)
---

### Задание 2
- Запустите три simple python сервера на своей виртуальной машине на разных портах
- Настройте балансировку Weighted Round Robin на 7 уровне, чтобы первый сервер имел вес 2, второй - 3, а третий - 4
- HAproxy должен балансировать только тот http-трафик, который адресован домену example.local
- На проверку направьте конфигурационный файл haproxy, скриншоты, где видно перенаправление запросов на разные серверы при обращении к HAProxy c использованием домена example.local и без него.

---

[haproxy.cfg](configs/task2/haproxy.cfg) переместить в `/etc/haproxy/haproxy.cfg`

Резутьтат

![Консоль](img/task2_1.png)
![Статистика](img/task2_2.png)
---

## Задания со звёздочкой*
Эти задания дополнительные. Их можно не выполнять. На зачёт это не повлияет. Вы можете их выполнить, если хотите глубже разобраться в материале.

---

### Задание 3*
- Настройте связку HAProxy + Nginx как было показано на лекции.
- Настройте Nginx так, чтобы файлы .jpg выдавались самим Nginx (предварительно разместите несколько тестовых картинок в директории /var/www/), а остальные запросы переадресовывались на HAProxy, который в свою очередь переадресовывал их на два Simple Python server.
- На проверку направьте конфигурационные файлы nginx, HAProxy, скриншоты с запросами jpg картинок и других файлов на Simple Python Server, демонстрирующие корректную настройку.

---

[haproxy.cfg](configs/task3/haproxy.cfg) переместить в `/etc/haproxy/haproxy.cfg`

[example-http.conf](configs/task3/nginx/example-http.conf) переместить в `/etc/nginx/conf.d/example-http.conf`

Резутьтат

![Консоль](img/task3_1.png)
![Статистика](img/task3_2.png)
---

### Задание 4*
- Запустите 4 simple python сервера на разных портах.
- Первые два сервера будут выдавать страницу index.html вашего сайта example1.local (в файле index.html напишите example1.local)
- Вторые два сервера будут выдавать страницу index.html вашего сайта example2.local (в файле index.html напишите example2.local)
- Настройте два бэкенда HAProxy
- Настройте фронтенд HAProxy так, чтобы в зависимости от запрашиваемого сайта example1.local или example2.local запросы перенаправлялись на разные бэкенды HAProxy
- На проверку направьте конфигурационный файл HAProxy, скриншоты, демонстрирующие запросы к разным фронтендам и ответам от разных бэкендов.

---

[haproxy.cfg](configs/task4/haproxy.cfg) переместить в `/etc/haproxy/haproxy.cfg`

Резутьтат

![Консоль](img/task4_1.png)
![Статистика](img/task4_2.png)

---
