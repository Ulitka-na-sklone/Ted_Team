# Лабораторная работа №3

## Часть 1. Поднятие Postgres
1. Создание и поднятие docker контейнеров:
![image1](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/1.jpg)
2. Определение master и slave ноды (master - pg_slave, slave - pg_master)
![image2](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/2.png)
![image3](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/3.jpg)
3. Проверка, что зукипер запустился
![image4](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/4.jpg)

## Часть 2. Репликации
4. Подключение к нодам постгреса
![image5](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/5.png)
![image6](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/6.jpg)
5. В ноду лидера кластера (pg_slave) добавляем таблицу и вставляем в неё данные
![image7](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/7.jpg)
![image8](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/8.jpg)
6. Проверяем, что в pg_master также создалась эта таблица с теми же данными
![image9](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/9.jpg)
7. Неудачно пытаемся удалить строчку из таблицы подключения pg_master
![image10](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/10.jpg)

## Часть 3. Высокая доступность и HAProxy
8. Перезапускаем docker контейнеры после добавления необходимых конфигурационных файлов и обновления docker-compose.yml для HAProxy
![image11](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/11.jpg)
9. Проверяем перераспределение ролей
![image12](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/12.jpg)
![image13](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/13.jpg)
10. Проверяем Zookiper
![image14](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/14.png)
11. Создаём подключение к psql_entrypoint (haproxy)
![image15](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/15.jpg)
12. Пытаемся заселектить данные из мастер-ноды (получилось!)
![image16](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/16.jpg)

## Задание
13. Отключаю мастер-ноду командой `docker stop pg-slave`
14. Наблюдаю за логами pg-master и haproxy. В логах у pg-master замечаю, patroni перераспределил роли, и теперь pg-master является лидером.
![image17](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/17.jpg)
![image18](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/18.jpg)
15. В entrypont-подключение добавляю новую строчку, которая дублируется и в pg-master
![image19](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/19.jpg)
![image20](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR3/pic/20.jpg)

## Ответы на вопросы
1. **Порты 8008 и 5432 вынесены в разные директивы, expose и ports. По сути, если записать 8008 в ports, то он тоже станет exposed. В чем разница?**

Порты в директивах expose доступны только в пределах сети docker compose, а в директивах ports порты будут открыты на хост-машины, и будут доступны извне.

2. **При обычном перезапуске композ-проекта, будет ли сбилден заново образ? А если предварительно отредактировать файлы postgresX.yml? А если содержимое самого Dockerfile? Почему?**

Compose образы не пересобираются автоматически при обычном перезапуске проекта, если не используется флаг --build.
Изменения в postgresX.yml влияют на настройки контейнеров и применяются сразу при перезапуске проекта — при этом образ пересобираться не будет. Если изменить содержимое Dockerfile, то образ также требует пересборки с флагом --build.
