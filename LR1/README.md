# ЛР 1. Loki + Zabbix + Grafana

## Ход работы:
1. Созданы файлы `docker-compose.yml`, `promtail_config.yml`, `template.yml` для дальнейшей работы.
2. Подняты контейнеры при помощи `docker compose`
![image 1](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/1.jpg)
![image 2](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/2.png)
3. Создана админка в NextCloud и проверили логи
![image 3](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/3.jpg)
4. Проверили promtail в логах
![image 4](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/4.jpg)
5. Настроили общение между заббиксом и некстклаудом по своим коротким именам внутри докеровской сети
![image 5](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/5.png)
6. Импортировали шаблон в zabbix
![image 6](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/6.jpg)
7.Создали новый хост и олучили первые данные
![image 7](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/7.jpg)
8. Установили плагин для графаны
![image 8](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/8.jpg)
9. Подключили дата сурсы и проверили их работу
![image 9](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/9.jpg)
![image 10](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/10.jpg)
![image 11](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/11.jpg)
![image 12](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/12.jpg)
![image 13](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/13.jpg)
10. Сделали визуализацию в виде графика и таблицы.
![image 14](https://github.com/Ulitka-na-sklone/Ted_Team/blob/main/LR1/pic/14.jpg)

## Ответы на вопросы
1. SLO (Service Level Objectives) – это желаемое, целевое значение SLI. При установке SLO необходимо указывать реально достижимое значение для каждого конкретного SLI.
   SLA (Service Leel Agreement) - соглашение, описывающее уровень качества предоставленной услуги.
3. Инкрементальный бэкап сохраняет изменения с последнего любого бэкапа, дифференциальный — с последнего полного.
4. Мониторинг — это часть observability. Мониторинг отслеживает известные показатели, а observability уже отслеживает их корреляцию и произоводит диагностику не одного конкретного показателя, а всей системы целиком.
