## Интеграция с nginx

1. Файл формы авторизации берем из `html/signin.html`

   - Чтобы nginx мог к нему обращаться копируем в `/var/www/html/` либо задаем другой `server.root`

2. Модуль конфигурации виртуального хостинга берем из `etc/nginx/sites-enabled/localhost.conf`
  
   - копируем `localhost.conf` в `/etc/nginx/sites-available/` на сервере
   - создаем ссылку на `/etc/nginx/sites-available/localhost.conf` в `/etc/nginx/sites-enabled/`
   
3. После перезапуска nginx прочитает свой общий файл конфигурации `/etc/nginx/nginx.conf` и применит файлы виртуального хостинга из `sites-enabled`.

По адресу [http://localhost/signin](http://localhost/signin) происходит отдача файла `/var/www/html/signin.html`

Остальные запросы перенаправляются к `localhost:8080`

Для тестирования можно использовать данные:
  - логин: `admin`, `manager`, `user`
  - пароль `1234`