# Текущее состояние

- Дата инициализации: 2026-11-23.
- Курс: Hibernate ORM изнутри.
- Hibernate progress: **0% — ни один урок Hibernate не пройден в рамках этого репозитория**.
- Активная фаза: A — архитектура и bootstrap.
- Следующий урок: **H00 — ориентация в Hibernate и карта архитектуры**.
- Статус H00: `NOT_STARTED`.
- Целевая версия: Hibernate ORM `7.4.17.Final`.
- Java: `17`.

## Уже закрытые предпосылки

PostgreSQL, JDBC, JDBC transactions/MVCC, connection pool/HikariCP и Spring JDBC `JdbcTemplate`.

## Точное следующее действие

Начать H00: объяснить разницу ORM / Hibernate ORM / Jakarta Persistence; native Hibernate API (`Session`, `SessionFactory`) vs JPA API (`EntityManager`, `EntityManagerFactory`); обозначить boot-time и runtime. Дать первую небольшую задачу: нарисовать/объяснить путь одного вызова `find` на уровне верхнеуровневых компонентов, пока без разбора внутренних методов и без написания проекта.

## Ограничения

- Не продолжать предыдущий самодельный MiniEntityManager.
- Не считать изученными Persistence Context, Dirty Checking, `persist`, `flush` или другие темы Hibernate из прежних разговоров.
- Не использовать Spring до конца Hibernate Core и Jakarta Persistence.
- Любое утверждение о внутренних классах проверять по версии 7.4.17.Final.

## Незакрытые вопросы

Пока нет: курс ещё не начат.
