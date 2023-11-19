# Представляю вашему вниманию yandex_fwork. 
# Это мой дипломный проект на курсе Инженер по тестированию +
# Яндекс Практикум

Описание проекта:

# 1. Тестирование функциональности веб-приложения
Чек лист для функционального тестирования web приложения (файл в репозитории)
# 2. Ретест багов в мобильном приложении. Ответ приложен в итоговый отчет.
Регресс мобильного приложения (файл в репозитории)
# 3. Регрессионное тестирование мобильного приложения по готовым тест-кейсам. Ответ приложен в итоговый отчет.
Регресс мобильного приложения (файл в репозитории)
# 4. Работа с базой данных
Запросы расположены в файле Base.sql (директория \yandex_fwork)

Задание 1
Представь: тебе нужно проверить, отображается ли созданный заказ в базе данных.
Для этого: выведи список логинов курьеров с количеством их заказов в статусе «В доставке» (поле inDelivery = true). 

запрос:

          SELECT c.login, COUNT(o.id) AS "deliveryCount" 
          FROM "Couriers" AS c 
          LEFT JOIN "Orders" AS o ON c.id = o."courierId" 
          WHERE o."inDelivery" = true 
          GROUP BY c.login;

Скриншот результата запроса Base_request1 sql.png (директория \yandex_fwork)

Задание 2

Ты тестируешь статусы заказов. Нужно убедиться, что в базе данных они записываются корректно.
Для этого: выведи все трекеры заказов и их статусы. 
Статусы определяются по следующему правилу:
Если поле finished == true, то вывести статус 2.
Если поле canсelled == true, то вывести статус -1.
Если поле inDelivery == true, то вывести статус 1.
Для остальных случаев вывести 0.

запрос:

           SELECT track, 
              CASE 
	        WHEN finished = true THEN 2 
	        WHEN cancelled = true THEN -1 
	        WHEN "inDelivery" = true THEN 1 
	  ELSE 0 END AS status 
          FROM "Orders";

Скриншот результата запроса Base_request2 sql.png (директория \yandex_fwork)
# 5. Автоматизация теста.

Для запуска теста необходимо в файл configuration скопировить URLстенда вида 
https://7b6b5ade-dbda-4523-aad6-50978727d2a9.serverhub.praktikum-services.ru

В файле sendor_stand_request нажать кнопку Run 

Скриншот автоматизации  Autotestrpy1.png, Autotestrpy2.png (директория \yandex_fwork)
      
Дополнительно в репозитории содержится:
Скриншот отправки запросов Postman: Postman_primer.png  (директория \yandex_fwork)
Чек лист для функционального тестирования web приложения
Регресс мобильного приложения
