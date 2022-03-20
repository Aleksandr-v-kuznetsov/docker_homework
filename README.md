# docker_homework
# 1 Лекция
Написать Dockerfile для frontend располагается в директории /frontend, собрать и запустить

`cd frontend`<br/>
`docker build . -t frontend`<br/>
`docker run -ti -p 3000:3000 frontend`<br/>
http://localhost:3000/ is working

# 2 Лекция
Написать Dockerfile для backend который располагается в директории /lib_catalog(для сборки контейнера необходимо использовать файл /lib_catalog/requirements.txt), для работы backend необходим postgresql, т.е. необходимо собрать 2 контейнера:
1. backend
2. postgresql

Осуществить сетевые настройки, для работы связки backend и postgresql

`docker pull postgres`<br/>
`docker network create --subnet 172.18.0.0/24 --gateway 172.18.0.1 homework_t2`<br/>
`docker run --name database -e POSTGRES_PASSWORD=homework -d --network homework_t2 postgres`<br/>
`docker build . -t homework_t2_backend`<br/>
`docker run -d --rm -p 8000:8000 --network homework_t2 --name homework_t2_backend homework_t2_backend`<br/>
http://localhost:8000/api/v1/lib/ is working

# 3 Лекция
Написать docker-compose.yaml, для всего проекта, собрать и запустить

# Критерий оценки финального задания
1. Dockerfile должны быть написаны согласно пройденным best practices
2. Для docker-compose необходимо использовать локальное image registry
3. В docker-compose необходимо сетевые настройки 2 разных интерфейса(bridge), 1 - для фронта, 2 - для бека с postgresql

4.* Осущиствить сборку проекта самим docker-compose команда docker-compose build(при использовании этого подхода необходимо исключить 2 пункт из критерии оценки)
