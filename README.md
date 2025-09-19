# local-gitlabCI

После запуска docker compose 
Запустить регистарцию ранера 
``` bash
docker exec -ti gitlab-runner gitlab-runner register --non-interactive \
        --url $CI_SERVER_URL   \
        --registration-token $REGISTRATION_TOKEN   \
        --executor docker
        --docker-image $DOCKER_IMAGE   \
        --tag-list $RUNNER_TAG_LIST \
        --name $RUNNER_NAME
```
