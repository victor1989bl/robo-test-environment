1. склонировать проект 
2. Проект настроен на адрес http://robo-test.local/ чтобы изменить его нужно поправить конфиг nginx (./conf.d/robo-test.conf) и конфиг приложения (./env/env.backend).
	прописать в hosts нужный адрес
3. запустить окружение `docker-compose up -d`
4. создать бд и заполнить тестовыми данными `docker-compose exec backend php artisan migrate --seed`
5. для запуска автоматической оплаты каждый час добавить в крон запуск шедулера `* * * * * /usr/bin/docker-compose -f /path/to/project/docker-compose.yml exec -T backend php artisan schedule:run >> /dev/null 2>&1`
6. pfofit