# Политика конфиденциальности для Google Play (GitHub Pages)

Готовая статичная страница: `index.html` (EN) и `ru.html` (RU). Без скриптов, без внешних ресурсов и
шрифтов — ничего не грузит со стороны и не собирает статистику.

## Перед публикацией

1. Заменить `CONTACT_EMAIL` в **обоих** файлах на настоящий адрес (по два вхождения: текст и `mailto:`):

   ```powershell
   (Get-Content index.html,ru.html) -replace 'CONTACT_EMAIL','you@example.com' | Set-Content ...
   ```

   или просто найти и заменить в редакторе.
2. Проверить дату «Обновлено» в обоих файлах, если публикуете позже.

## Публикация

```bash
cd source/store/github-pages
git init
git add .
git commit -m "Office Rush: политика конфиденциальности"
git branch -M main
git remote add origin https://github.com/<аккаунт>/office-rush-legal.git
git push -u origin main
```

Репозиторий должен быть **публичным** (бесплатные Pages). Дальше на GitHub:
**Settings → Pages → Source: Deploy from a branch → Branch: `main`, папка `/ (root)` → Save.**

Через минуту страница откроется по адресу:

- EN — `https://<аккаунт>.github.io/office-rush-legal/`
- RU — `https://<аккаунт>.github.io/office-rush-legal/ru.html`

Если назвать репозиторий `<аккаунт>.github.io`, адрес будет короче: `https://<аккаунт>.github.io/`.

## Куда вставить ссылку

- Google Play Console → **App content → Privacy policy** — URL английской страницы.
- `source/store/google_play.md` — строка «Политика конфиденциальности (URL)».
- `source/store/rustore.md` — раздел «Политика конфиденциальности» (RuStore тоже просит ссылку).
- Если политика на сайте магазина обязательна на русском — давать ссылку `ru.html`.

## Важно

Политика верна, пока в сборке **нет рекламы и аналитики**: Яндекс-реклама в релизе выключена
(`[editor_plugins]` в `project.godot`), интернет игра не использует. Если включить рекламу Яндекса,
раздел 4 придётся переписать: рекламный SDK собирает рекламный идентификатор устройства и требует
согласия по GDPR/CCPA, а в Play — заполнения Data safety.
