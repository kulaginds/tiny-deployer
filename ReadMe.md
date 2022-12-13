# Tiny Deployer
Systemd демон для деплоя приложения из Github репозитория на локальный сервер (за NAT).

## Принцип работы
1. Фоновый процесс раз в минуту опрашивает изменения в Github-пакете на предмет [новых версий](https://docs.github.com/en/rest/packages?apiVersion=2022-11-28#list-package-versions-for-a-package-owned-by-an-organization).
2. Когда процесс замечает новую версию, запускает процесс деплоя.  
   В первом варианте это просто будут команды:
   ```bash
   git pull
   docker-compose pull
   docker-compose up -d
   ```
Проекты с Github-репозиториями будут описаны в yaml-конфиге фонового процесса.  
Каждый проект будет деплоиться в свою папку.
