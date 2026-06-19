# План тестирования локального OpenCart

## Объект тестирования
Локальный сайт OpenCart, поднятый через `docker-compose.yml` из задания.

## Базовый адрес
По умолчанию используется `http://localhost:8081`. Адрес можно изменить через переменную `BASE_URL` или параметр pytest `--base-url`.

## Проверяемые области
1. Открытие главной страницы.
2. Поиск товаров.
3. Карточка товара.
4. Добавление товара в корзину.
5. Корзина.
6. Форма обратной связи.
7. Форма регистрации.
8. JavaScript-прокрутка, cookies.

## Набор автотестов
| № | Тест | Что проверяется |
|---|------|-----------------|
| 1 | `test_home_page_opened` | Главная страница открывается, логотип и поиск доступны |
| 2 | `test_header_search_input_accepts_text` | Поле поиска принимает текст через `send_keys` |
| 3 | `test_search_existing_product_returns_results` | Поиск существующего товара возвращает результат |
| 4 | `test_search_nonexistent_product_shows_empty_result` | Поиск несуществующего товара показывает пустой результат |
| 5 | `test_product_card_opens_from_search` | Карточка товара открывается из результатов поиска |
| 6 | `test_product_quantity_field_accepts_value` | Поле количества в карточке товара принимает значение |
| 7 | `test_add_product_to_cart_shows_success_message` | Товар добавляется в корзину, появляется сообщение об успехе |
| 8 | `test_shopping_cart_page_available` | Страница корзины доступна |
| 9 | `test_contact_page_form_fields_are_present` | На странице контактов есть поля формы |
| 10 | `test_contact_form_validation_for_empty_submit` | Пустая форма контактов вызывает валидацию |
| 11 | `test_registration_page_form_fields_are_present` | Форма регистрации содержит обязательные поля |
| 12 | `test_javascript_scroll_to_footer` | JavaScript-прокрутка работает |
| 13 | `test_browser_cookie_can_be_added_and_read` | Selenium умеет добавить и прочитать cookie |
