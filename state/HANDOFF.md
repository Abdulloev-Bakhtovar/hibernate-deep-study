# HANDOFF — передача контекста новому агенту

## Цель

Научить ученика понимать Hibernate ORM изнутри, читать исходники и осознанно пользоваться аннотациями/API. Далее изучить Jakarta Persistence, затем Spring ORM и Spring Data JPA.

## Зафиксированная среда

- Hibernate ORM `7.4.17.Final` (зафиксировано 2026-11-23).
- Java 17.
- PostgreSQL — существующая локальная база ученика.
- Maven.

## Что уже изучено до Hibernate

PostgreSQL, JDBC, JDBC transactions/MVCC, HikariCP/connection pool и Spring JDBC `JdbcTemplate`. Не повторять с нуля.

## Что НЕ изучено

Весь Hibernate. Предыдущие обсуждения и реализация самодельных `EntityMetadata`, `PersistenceContext`, `DirtyChecker`, `MiniEntityManager`, `persist`, `flush` не засчитываются. Начать обучение по roadmap заново.

## Текущее положение

- Hibernate progress: 0%.
- Активный урок: H00 — ориентация в Hibernate и карта архитектуры.
- H00 ещё не начат.

## Следующее действие

Начать H00 по `lessons/00-orientation.md` (если карточки ещё нет — создать по `lessons/TEMPLATE.md` и `docs/COURSE_ROADMAP.md`). Объяснить ORM vs Hibernate ORM vs Jakarta Persistence, Hibernate native API vs EntityManager API, boot-time vs runtime. Дать одну небольшую проверку понимания.

## Обязательные ограничения

- Прочитать `AGENTS.md`.
- Не задавать заново вопросы об исходной подготовке.
- Не продолжать старый Mini ORM.
- Не использовать Spring до окончания Hibernate Core/JPA этапов.
- Проверять внутренности только по точному релизу 7.4.17.Final.
- После занятия обновить state-файлы через `/checkpoint`.

## Источники

См. `docs/SOURCE_POLICY.md` и `references/OFFICIAL_SOURCES.md`.
