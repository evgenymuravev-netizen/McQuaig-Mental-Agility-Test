# Тесты и диагностики

Четыре статических веб-приложения: тренажёр Mental Agility Test, оценка
системного аналитика, тест эффективности работы с ИИ и командная диагностика
стратегии и культуры. Всё работает в браузере, без сборки и зависимостей,
открывается даже по `file://`. Результаты остаются на устройстве.

**Сайт:** <https://evgenymuravev-netizen.github.io/McQuaig-Mental-Agility-Test/>

| Приложение | Ссылка | Что это |
|---|---|---|
| Mental Agility Test | [`/mmat/`](https://evgenymuravev-netizen.github.io/McQuaig-Mental-Agility-Test/mmat/) · [гайд](https://evgenymuravev-netizen.github.io/McQuaig-Mental-Agility-Test/mmat/guide.html) | Тренировка в формате McQuaig MMAT: бесплатный 5-минутный тест и десять форм по 15 минут, разбор каждого ответа, адаптивный раунд по слабым темам |
| System Analyst Assessment | [`/sysanalyst/`](https://evgenymuravev-netizen.github.io/McQuaig-Mental-Agility-Test/sysanalyst/) · [профиль](https://evgenymuravev-netizen.github.io/McQuaig-Mental-Agility-Test/sysanalyst/profile.html) · [работодателям](https://evgenymuravev-netizen.github.io/McQuaig-Mental-Agility-Test/sysanalyst/employers.html) · [под вакансию](https://evgenymuravev-netizen.github.io/McQuaig-Mental-Agility-Test/sysanalyst/tailor.html) | 225 вопросов: API/REST, протоколы, сети/OSI, очереди, базы данных; первые 25 бесплатно; RU/EN; кабинеты кандидата и работодателя, тест под вакансию |
| AI Efficiency Test | [`/ai-efficiency/`](https://evgenymuravev-netizen.github.io/McQuaig-Mental-Agility-Test/ai-efficiency/) | Насколько эффективно человек работает с ИИ в роли PM / системного аналитика / проджект-менеджера; двусторонняя шкала: штраф и за недоиспользование, и за слепое доверие |
| Опрос по контурам | [`/contours/`](https://evgenymuravev-netizen.github.io/McQuaig-Mental-Agility-Test/contours/) · [отчёт](https://evgenymuravev-netizen.github.io/McQuaig-Mental-Agility-Test/contours/report.html) | Не тест со счётом: меряет сходимость понимания стратегии (К1) и культуры (К2) в команде; анонимность слоями, агрегат при N ≥ 5, опциональный бэкенд приёма с ИИ-кодировкой открытых ответов |

Подробности по каждому приложению — в его `README.md`. Устройство, решения и
границы описаны там же (`contours/DESIGN-v0.2.md`, `mmat/STRATEGY.md`,
`sysanalyst/INTEGRITY.md` и др.).

## Проверки

Node 18+, без зависимостей:

```sh
node mmat/validate.mjs && node mmat/check-answers.mjs && node mmat/test-engine.mjs
node sysanalyst/validate.mjs && node sysanalyst/test-engine.mjs
node ai-efficiency/test-engine.mjs
(cd contours && node test-metrics.mjs && node test-runner.mjs && node test-report.mjs && node test-worker.mjs)
```

`mmat/standalone.html` и `sysanalyst/standalone.html` — однофайловые сборки;
после правок исходников пересобираются `node mmat/build-standalone.mjs` и
`node sysanalyst/build-standalone.mjs`.

## Публикация

GitHub Pages через Actions (`.github/workflows/deploy.yml`): каждый push в
`main` выкладывает репозиторий целиком как статический сайт. Один раз нужно
включить Pages: **Settings → Pages → Build and deployment → Source: GitHub
Actions**.

## Происхождение

Выделено из `evgenymuravev-netizen/Digital_aristotle` вместе с историей:
сохранены только коммиты, затрагивающие эти четыре папки. Ссылки на PR в
сообщениях коммитов указывают на исходный репозиторий
(`evgenymuravev-netizen/Digital_aristotle#N`).

«McQuaig» и «MMAT» упоминаются только для описания формата теста. Тренажёр
независим и не связан с The McQuaig Institute®.
