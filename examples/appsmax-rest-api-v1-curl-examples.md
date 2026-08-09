# Примеры запросов к AppsMax REST API v1

Все значения в примерах вымышлены. Перед первым запросом замените
`YOUR_API_TOKEN`, `BOT_ID` и идентификаторы ресурсов значениями своей
организации.

## Проверить токен и организацию

```bash
curl --request GET \
  --url https://telegram.appsmax.ru/api/v1/me \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer YOUR_API_TOKEN'
```

## Получить ботов MAX

```bash
curl --request GET \
  --url 'https://telegram.appsmax.ru/api/v1/bots?driver=max&per_page=50' \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer YOUR_API_TOKEN'
```

Для Telegram используйте фактически доступное проекту значение фильтра,
описанное в текущей документации и ответах API. Не предполагайте одинаковость
возможностей двух каналов только по совпадению формата данных.

## Создать тестовую заявку

```bash
curl --request POST \
  --url https://telegram.appsmax.ru/api/v1/applications \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer YOUR_API_TOKEN' \
  --header 'Content-Type: application/json' \
  --data '{
    "bot_id": BOT_ID,
    "source": "rest_api",
    "title": "Тестовая заявка интеграции",
    "channel": "website",
    "contact": {
      "name": "Тестовый контакт",
      "phone": "+70000000000",
      "email": "test@example.invalid"
    },
    "payload": {
      "comment": "Проверка интеграции без клиентских данных"
    }
  }'
```

Поле `bot_id` обязательно и должно принадлежать организации токена. Новая
заявка получает начальный статус по правилам AppsMax; задавать произвольный
статус верхнего уровня при создании не следует.

## Обработка лимита

При ответе `429 Too Many Requests` учитывайте `X-RateLimit-*`, делайте паузу и
используйте exponential backoff. Не повторяйте запросы плотным циклом.

## Перед production-запуском

- отделите токены чтения от токенов записи, если это возможно;
- передавайте только необходимые данные;
- проверьте роли оператора и обработчика персональных данных;
- зафиксируйте сроки хранения и удаления;
- не используйте метод кампаний без основания коммуникации и проверки правил
  конкретного канала;
- проверьте актуальную reference: <https://appsmax.ru/developers/>.
