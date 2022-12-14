План автоматизации тестирования

Преднастройка: 
1. запуcтить SUT (System Under Test)
2. открыть страницу покупки тура http://localhost:8080 (ссылка перехода на станицу покупки тура доступна только при запущенной SUT).

Карты, предоставленные для тестирования в файле data.json:

- номер: 4444 4444 4444 4441, статус: "APPROVED"
- номер: 4444 4444 4444 4442, статус: "DECLINED"

1. Перечень автоматизируемых сценариев

Позитивные сценарии: 
1) для оплаты по дебетовой карте со статусом "APPROVED":
- кликнуть кнопку "Купить"
- в поле "Номер карты" ввести 16 цифр
- в поле "Месяц" ввести двузначное числовое значение от 01 до 12
- в поле "Год" ввести двузначное числовое значение;
- в поле "Владелец" ввести допустимые значения из латинских букв, дефисов, пробелов
- в поле "CVC/CCV" ввести три цифры
- нажать кнопку "Отправить"
Ожидаемый результат: Оплата проходит(данные об оплате появляются в базе). Появляется сообщение об успешной покупке тура.

2) для оплаты по дебетовой карте со статусом "DECLINED":
- кликнуть кнопку "Купить"
- в поле "Номер карты" ввести 16 цифр
- в поле "Месяц" ввести двузначное числовое значение от 01 до 12
- в поле "Год" ввести двузначное числовое значение;
- в поле "Владелец" ввести допустимые значения из латинских букв, дефисов, пробелов
- в поле "CVC/CCV" ввести три цифры
- нажать кнопку "Отправить"
  Ожидаемый результат: Оплата не проходит(в базе данных появляется информация, что покупка отклонена). Появляется
  сообщение об ошибке.

3) для оплаты в кредит по карте со статусом "APPROVED":
- кликнуть кнопку "Купить в кредит"
- в поле "Номер карты" ввести 16 цифр
- в поле "Месяц" ввести двузначное числовое значение от 01 до 12
- в поле "Год" ввести двузначное числовое значение;
- в поле "Владелец" ввести допустимые значения из латинских букв, дефисов, пробелов
- в поле "CVC/CCV" ввести три цифры
- нажать кнопку "Отправить"
  Ожидаемый результат: Появляется сообщение об одобрении операции банком.

4) для оплаты в кредит по карте со статусом "DECLINED":
- кликнуть кнопку "Купить в кредит"
- в поле "Номер карты" ввести 16 цифр
- в поле "Месяц" ввести двузначное числовое значение от 01 до 12
- в поле "Год" ввести двузначное числовое значение;
- в поле "Владелец" ввести допустимые значения из латинских букв, дефисов, пробелов
- в поле "CVC/CCV" ввести три цифры
- нажать кнопку "Отправить"
  Ожидаемый результат: Появляется сообщение об ошибке. Банк отказал в проведении операции"

Негативные сценарии:
1) отправка пустой формы:
- кликнуть кнопку "Купить"
- нажать кнопку "Отправить"
Ожидаемый результат: отправки данных не произойдет. Под незаполнеными полями появятся сообщения "Поле обязательно для заполнения".

2) отправка формы с одним из пустых (не заполненых) полей:
- кликнуть кнопку "Купить"
- поле "Номер карты" остается пустым, остальные поля заполняются валидными данными
- нажать кнопку "Отправить"
  Ожидаемый результат: отправки данных не произойдет. Под незаполненым полем появится сообщение "Поле обязательно для заполнения".

Повторить такие же вариации с отправкой формы, но с другим пустым полем: месяц, год, владелец или CVC/CCV.  

3) отправка формы с одним из пустых (не заполненых) полей:
- кликнуть кнопку "Купить в кредит"
- поле "Номер карты" остается пустым, остальные поля заполняются валидными данными
- нажать кнопку "Отправить"
  Ожидаемый результат: отправки данных не произойдет. Под незаполненым полем появится сообщение "Поле обязательно для заполнения".

Повторить такие же вариации с отправкой формы, но с другим пустым полем: месяц, год, владелец или CVC/CCV.

4) отправка формы с одним полем из невалидных данных:
- кликнуть кнопку "Купить"
- поле "Номер карты" заполнить невалидными данными (например латинскими буквами), остальные поля заполняются валидными данными
- нажать кнопку "Отправить"
  Ожидаемый результат: отправки данных не произойдет. Под полем "Номер карты" появится сообщение "Неверный формат".

5) отправка формы с одним полем из невалидных данных:
- кликнуть кнопку "Купить"
- поле "Месяц" заполнить невалидными данными (например числом 23), остальные поля заполняются валидными данными
- нажать кнопку "Отправить"
  Ожидаемый результат: отправки данных не произойдет. Под полем "Месяц" появится сообщение "Неверно указан срок действия карты".

6) отправка формы с одним полем из невалидных данных:
- кликнуть кнопку "Купить"
- поле "Год" заполнить невалидными данными (например ввести одно значение из цифры 9), остальные поля заполняются валидными данными
- нажать кнопку "Отправить"
  Ожидаемый результат: отправки данных не произойдет. Под полем "Год" появится сообщение об ошибке, что поле заполнено неверно.

7) отправка формы с одним полем из невалидных данных:
- кликнуть кнопку "Купить"
- поле "CVC/CCV" заполнить невалидными данными (например латинскими буквами), остальные поля заполняются валидными данными
- нажать кнопку "Отправить"
  Ожидаемый результат: отправки данных не произойдет. Под полем "CVC/CCV" появится сообщение об ошибке, что поле заполнено неверно.

8) отправка формы с одним полем из невалидных данных:
- кликнуть кнопку "Купить"
- поле "Владелец" заполнить невалидными данными (например буквами и спец.символами ?#$), остальные поля заполняются валидными данными
- нажать кнопку "Отправить"
  Ожидаемый результат: отправки данных не произойдет. Под полем "Владелец" появится сообщение "Введите допустимые значения из латинских букв, дефисов, пробелов".

Аналогично протестировать все те же негативные сценарии для кнопки "Купить в кредит".

2. Перечень используемых инструментов с обоснованием выбора:
   1). Git и GitHub (с заранее подготовленным .gitignore) — для хранение кода, в том числе автотестов;
   2). IntelliJ IDEA, удобная среда подготовки авто-тестов;
   3). JDK 11 - программный пакет, который нужен для создания Java-приложений, т.к. потребуются инструменты работающие с Java;
   4). Gradle - система управление проектами;
   5). JUnit 5 - платформы для написания автотестов и их запуска;
   6). Selenide - фреймворк для процесса автоматизированного тестирования ПО. Позволяет комфортно создавать програмный код при тестировании веб-интерфейса;
   7). Faker - библиотека для генерация тестовых данных;
   8). Lombok - плагин для добавления дополнительных аннотаций;
   9). Docker Desktop - приложение, которое предоставляет среду для сборки и запуска контейнеризированных приложений; 
      Необходимо для запуска симулятора банковских сервисов, который может принимать запросы в нужном формате и генерировать ответы.
   10). Allure - наглядная визуализация создания отчетов о выполнении авто-тестов;
       
3. Перечень и описание возможных рисков при автоматизации
   - Трудности при настройке инструментов, необходимых для автоматизированного тестирования (одновременная поддержка 2-х СУБД, запуск контейнеров и SUT);
   - Отсутствие документации на тестируемое приложение;
   - Зависимость авто-тестов от текущей реализации веб-элементов (при возможном изменении структуры сайта, в ходе реализации проекта, есть риск что авто-тесты упадут;
   

4. Интервальная оценка с учётом рисков (в часах):

Для осуществления автоматизации с учётом вышеназванных рисков, потребуется примерно 256 часов.

5. План сдачи работ:

1). Подготовка к проведению тестирования (запуск SUT, подготовка плана автоматизации) - 3 дня;
2). Написание и прогон авто-тестов - 10 дней;
3). Составление Issue - 3 дня;
4). Оформление отчёта по итогам автоматизации - 3 дня.


