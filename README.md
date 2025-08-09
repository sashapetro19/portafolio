# UX/UI Portfolio — Next.js

Актуальна версія портфоліо з багатомовністю, фільтрами, кейсами, темною темою, анімаціями та інтеграцією з WordPress (опційно).

## Особливості
- Багатомовність (es, en, uk, ru) з селектором мови та hreflang.
- Сторінки: Home, About, Portfolio (+деталі), Services, Contact.
- Портфоліо: пошук, фільтри, сторінки кейсів, режим «Presentation».
- Темна тема (persist), micro‑interactions, reveal, parallax/tilt.
- Аналітика (легка, готова до заміни), OG‑зображення.
- Інтеграція з WordPress REST (опційно) з локальним fallback.

## Швидкий старт (локально)
\`\`\`bash
npm i
npm run dev
# або
pnpm i
pnpm dev
\`\`\`

Відкрийте http://localhost:3000

## Конфігурація (опційно)
Щоб підтягувати реальні проєкти з WordPress:
- Додайте змінну середовища у вашому хості/CI:
  - WP_REST_URL=<ваш-домен-WordPress> (наприклад, https://example.com)
- Ендпоінт очікується як: `${WP_REST_URL}/wp-json/wp/v2/project?per_page=100&_embed`

Якщо змінної немає, використовується локальний fallback (public/data/projects.json).

## GitHub CI
У репозиторії є workflow `.github/workflows/ci.yml`, що:
- Встановлює Node 20
- Інсталює залежності
- Перевіряє типи (tsc) та збирає проект (next build)

Бейдж додасться автоматично після першого запуску.

## GitHub Pages (зауваження)
Проєкт має API‑роути (/api/*) і динамічні можливості (OG, аналітика). GitHub Pages — статичний хостинг, тому:
- UI працюватиме, але серверні роутери не будуть доступні.
- Для статичного режиму ми додали fallback на `public/data/projects.json`.
- Рекомендовано деплой на Vercel (одним кліком із GitHub) для повного функціоналу.

## Скрипти
- dev — запуск розробки
- build — продакшен збірка
- start — запуск продакшен сервера (на платформах, що підтримують SSR)
- typecheck — перевірка типів

## Структура
- app/ — Next.js App Router сторінки
- components/ — UI/блоки
- lib/ — i18n, метадані проєктів
- public/ — статичні файли (в т.ч. data/projects.json для fallback)
- .github/ — CI, шаблони issues/PR

## Контриб’юції
Див. CONTRIBUTING.md та PR шаблон.

## Ліцензія
MIT — див. LICENSE
