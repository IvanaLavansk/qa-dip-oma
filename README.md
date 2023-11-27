# Дипломный проект по профессии «Тестировщик»
- [Задание](https://github.com/IvanaLavansk/qa-dip-oma/blob/main/docs/Task.md)
- [План тестирования](https://github.com/IvanaLavansk/qa-dip-oma/blob/main/docs/Plan.md)

- [Отчётные документы по итогам тестирования](https://github.com/IvanaLavansk/qa-dip-oma/blob/main/docs/Report.md)
- [Отчётные документы по итогам автоматизации](https://github.com/IvanaLavansk/qa-dip-oma/blob/main/docs/Summary.md)

## Описание приложения
Приложение — это веб-сервис, который предлагает купить тур по определённой цене двумя способами:

1) Обычная оплата по дебетовой карте.
2) Уникальная технология: выдача кредита по данным банковской карты.


Само приложение не обрабатывает данные по картам, а пересылает их банковским сервисам:

- сервису платежей, далее Payment Gate;
- кредитному сервису, далее Credit Gate.

Приложение в собственной СУБД должно сохранять информацию о том, успешно ли был совершён платёж и каким способом. Данные карт при этом сохранять не допускается.

### Для выполнения работы необходимо:

1) Установить [Google Chrome](https://www.google.ru/chrome/);
2) Установить [IntelliJ IDEA](https://www.jetbrains.com/ru-ru/idea/download/?section=windows#section=windows);
3) Установить [Github](https://desktop.github.com/);
4) Установить [Docker Desktop](https://www.docker.com/).

### Запуск тестов 
1) Клонировать репозиторий командой `git clone https://github.com/TatianaSm77/Diploma`
2) Открыть проект в IntelliJ IDEA;
3) Создать контейнеры в скопированном проекте `docker-compose up -d`;


#### Для проверки MySQL:
1) Запустить jar-файл с базой данных MySQL командой: `java "-Dspring.datasource.url=jdbc:mysql://185.119.57.126:3306/app" -jar artifacts/aqa-shop.jar`;

2) Убедиться в готовности системы. Приложение должно быть доступно по адресу: `http://localhost:8080/`;

3) В новой вкладке терминала запустить тесты командой: `./gradlew clean test "-Ddb.url=jdbc:mysql://185.119.57.126:3306/app"` ;

4) Для создания отчета запустить команду:`./gradlew allureServe`, `./gradlew allureReport`

#### Для проверки PostgreSQL:
1) В новой вкладке терминала запустить тестируемое приложение командой: `java "-Dspring.datasource.url=jdbc:postgresql://185.119.57.126:5432/app" -jar artifacts/aqa-shop.jar`;

2) Убедиться в готовности системы. Приложение должно быть доступно по адресу: `http://localhost:8080/`;

3) В новой вкладке терминала запустить тесты командой: `.\gradlew clean test "-Ddb.url=jdbc:postgresql://185.119.57.126:5432/app"`  ;

4) Для создания отчета запустить команду: `./gradlew allureServe`,`./gradlew allureReport`

 - Для остановки приложений использовать команду `Cntrl C`.
- Для удаления контейнеров использовать команду `docker-compose down`