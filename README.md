#  Проект Kittygram
![Badge](https://github.com/Amir800S/kittygram_final/actions/workflows/kittygram_workflow.yml/badge.svg)
### Через Kittygram возможно создание, редактирование и просмотр котиков!
Использованные технологии:

![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)

### Как пользоваться проектом?
Клонируем репозиторий:
```python
git clone git@github.com:svkiruck/kittygram_final.git
```
Переходим в директорию проекта и запускаем его:
```python
cd kittygram_final
```
Запускаем проект в режиме демона:
```python
sudo docker compose -f docker-compose.production.yml up -d
```
Далее нужно собрать статику проекта и выполнить миграции:
```python
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```
Проект настроен на работу на 9000 порту поэтому необходимо изменить конфиг Nginx:
```python
nano /etc/nginx/sites-enabled/default
```
```python
location / {
    proxy_pass http://127.0.0.1:9000;
}
```
В файле kittygram_workflow.yml - настройки для GitHub Actions он находится:
```python
kittygram_final/.github/workflows/kittygram_workflow.yml
```

### Проект с котиками готов к работе!
