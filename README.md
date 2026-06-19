# Итоговая работа: Selenium + Docker + OpenCart

Проект содержит автотесты для локального сайта OpenCart, который поднимается через Docker Compose. Работа выполнена по заданию: поднять `docker-compose.yml`, изучить материалы по Selenium и написать минимум 10 автотестов для локального сайта.

## Состав репозитория

opencart-selenium-tests/
├── docker-compose.yml
├── requirements.txt
├── pytest.ini
├── TEST_PLAN.md
├── README.md
├── pages/
│   ├── base_page.py
│   ├── home_page.py
│   ├── search_page.py
│   ├── product_page.py
│   ├── contact_page.py
│   └── account_page.py
├── tests/
│   ├── conftest.py
│   └── test_opencart_ui.py
├── artifacts/
│   └── screenshots/
└── docs/
    └── Отчет.docx


## Что проверяют автотесты

В проекте подготовлено 13 автотестов, то есть больше минимального требования задания. Проверяются главная страница, поиск, карточка товара, корзина, форма контактов, форма регистрации, меню, футер, JavaScript-прокрутка и работа с cookies.

## 1. Запуск OpenCart через Docker

### Вариант через `.env`

Создать в корне проекта файл `.env` по примеру `.env.example`:

OPENCART_PORT=8081
PHPADMIN_PORT=8888
LOCAL_IP=localhost
BASE_URL=http://localhost:8081
HEADLESS=true

После этого выполнить:

docker compose up -d

Сайт должен открыться по адресу:

http://localhost:8081

phpMyAdmin должен открыться по адресу:

http://localhost:8888


### Вариант для Windows PowerShell

powershell
$env:OPENCART_PORT="8081"
$env:PHPADMIN_PORT="8888"
$env:LOCAL_IP="localhost"
docker compose up -d


Если сайт не открывается через `localhost`, нужно указать IP-адрес компьютера вместо `localhost` в переменной `LOCAL_IP`.

## 2. Установка зависимостей для автотестов

### Windows PowerShell

powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt

### macOS / Linux

python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

## 3. Запуск тестов

Обычный запуск:

pytest -v

Запуск с указанием адреса сайта:

pytest -v --base-url http://localhost:8081

Запуск с открытым браузером:

pytest -v --headed

## 4. Allure-отчет

Для формирования результатов Allure:

pytest --alluredir=allure-results

Для просмотра отчета нужно установить Allure CLI и выполнить:

allure serve allure-results

## 5. Скриншоты

При падении теста скриншот автоматически сохраняется в папку:

artifacts/screenshots/

В итоговом отчете оставлены пустые места под скриншоты. После локального запуска нужно вставить туда свои изображения: Docker, открытый OpenCart, результат `pytest`, Allure и GitHub-репозиторий.

## 6. Команды Docker

Проверить запущенные контейнеры:

docker compose ps

Остановить контейнеры:

docker compose down

Остановить контейнеры и удалить тома:

docker compose down -v



