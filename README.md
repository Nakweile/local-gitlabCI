Этот репозиторий предназначен для развёртывания локального стенда GitLab и регистрации собственного GitLab Runner с использованием Docker Compose.

Структура проекта
- my-first-ci-pipeline/
	- hello.py: Пример простого Python-скрипта для CI.
	- requirements.txt: Содержит список зависимостей проекта (в данном случае — pytest).
- my-gitlab-ci/
	- docker-compose.yml: Конфигурация для запуска GitLab и Runner.

##### Быстрый старт
1. Клонируйте репозиторий:

``` bash
git clone https://github.com/Nakweile/local-gitlabCI.git
cd local-gitlabCI/my-gitlab-ci
```
2. Запустите инфраструктуру через Docker Compose:

```
docker compose up -d
```
3. После запуска выполните регистрацию раннера:

``` bash
docker exec -ti gitlab-runner gitlab-runner register --non-interactive \
  --url $CI_SERVER_URL \
  --registration-token $REGISTRATION_TOKEN \
  --executor docker \
  --docker-image $DOCKER_IMAGE \
  --tag-list $RUNNER_TAG_LIST \
  --name $RUNNER_NAME
```
Все параметры (токены и переменные) указываются в .env файле или экспортируются в окружении.

4. Проверьте работоспособность пайплайна на примере из папки `my-first-ci-pipeline`.
