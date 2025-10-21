## 5.1 Проверка версии Docker

После установки Docker на вашей системе важно убедиться, что все компоненты работают корректно. Первый запуск Docker включает несколько шагов для проверки установки и начальной настройки.

Начнем с проверки версии Docker. Этот шаг подтверждает корректность установки и позволяет убедиться, что командная строка распознает команды Docker.

**1. Откройте терминал или командную строку:**

1. На Windows: откройте PowerShell или командную строку (CMD).
2. На macOS: откройте терминал (Terminal.app).
3. На Linux: откройте терминал.

**2. Введите команду для проверки версии:**

Terminal

```bash
sudo docker --version
```

В ответ вы увидите установленную версию Docker, например:

Terminal

```bash
Docker version 20.10.7, build f0df350
```

## 5.2 Запуск тестового контейнера

Следующий шаг — запуск тестового Docker-контейнера. Это позволит проверить работу Docker-демона и убедиться в возможности запуска контейнеров на вашем компьютере.

**1. Запуск тестового контейнера "hello-world":**

Terminal

```bash
docker run hello-world
```

При выполнении этой команды Docker загрузит образ "hello-world" из Docker Hub и запустит его в контейнере. Если образ отсутствует на вашем компьютере, система автоматически загрузит его.

**2. Ожидаемый результат:** При правильной работе Docker вы увидите следующее сообщение:

Terminal

```bash
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
1. The Docker client contacted the Docker daemon.
2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
   (amd64)
3. The Docker daemon created a new container from that image which runs the
   executable that produces the output you are currently reading.
4. The Docker daemon streamed that output to the Docker client, which sent it
   to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
$ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
https://hub.docker.com/

For more examples and ideas, visit:
https://docs.docker.com/get-started/
```

## 5.3 Проверка состояния Docker Daemon

Теперь вам нужно убедиться, что Docker Daemon работает.

**На Windows и macOS:**

Docker Desktop автоматически запускает Docker Daemon. Вы можете проверить его состояние. На Windows вы найдете значок Docker в системном трее (внизу экрана, рядом с часами). Щёлкните на него для проверки состояния. На macOS значок Docker расположен в строке меню в верхней части экрана рядом с системными индикаторами (Wi-Fi, громкость). При нормальной работе значок будет активным, без предупреждающих символов (например, жёлтого треугольника или красного крестика).

**На Linux:**

Введите команду для проверки состояния Docker Daemon:

Terminal

```bash
sudo systemctl status docker
```

Вы увидите вывод, показывающий статус службы Docker. Если Docker работает корректно, статус будет "active (running)".

## 5.4 Проверка сети Docker

Docker использует виртуальные сети для взаимодействия между контейнерами и внешним миром. Проверка сети Docker подтверждает, что контейнеры могут взаимодействовать через сеть.

**1. Список существующих сетей:**

Terminal

```bash
docker network ls
```

Вы увидите список сетей, созданных Docker по умолчанию:

Terminal

```bash
NETWORK ID          NAME                DRIVER              SCOPE
8d3d90a1e084        bridge              bridge                 local
9e3bdf739d23        host                   host                   local
a34e1b2f4c07        none                   null                    local
```

**2. Создание и проверка пользовательской сети:**

Создайте новую сеть:

Terminal

```bash
docker network create my_test_network
```

Проверьте, что сеть была создана:

Terminal

```bash
docker network ls
```

Вы увидите новую сеть `"my_test_network"` в списке.

## 5.5 Проверка томов Docker

Docker использует тома для постоянного хранения данных контейнеров. Проверка томов Docker подтверждает возможность создания и управления томами для хранения данных.

**Полезно:** том (volume) — это что-то типа виртуального жесткого диска. На реальной операционной системе он хранится в виде обычного файла.

**1. Список существующих томов:**

Terminal

```bash
docker volume ls
```

Вы увидите список существующих томов, если они есть.

**2. Создание и проверка пользовательского тома:**

Создайте новый том:

Terminal

```bash
docker volume create my_test_volume
```

Проверьте, что том был создан:

Terminal

```bash
docker volume ls
```

Вы увидите новый том `"my_test_volume"` в списке.

Первый запуск Docker и проверка установки — важные шаги, подтверждающие, что все компоненты настроены и функционируют корректно. После проверки версии Docker, запуска тестового контейнера, проверки состояния Docker Daemon, а также проверки сетей и томов Docker вы можете быть уверены, что система готова к работе с контейнерами и развертыванию приложений.