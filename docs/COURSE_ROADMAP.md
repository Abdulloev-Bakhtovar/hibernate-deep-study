# Дорожная карта курса

Статусы в начале курса: все темы Hibernate — `NOT_STARTED`. Переход к следующей фазе только после закрытия текущих контрольных точек. Порядок может уточняться, но изменения фиксируются в `state/DECISIONS.md`.

## Фаза A. Архитектурная ориентация и bootstrap

- **H00 — Карта Hibernate.** ORM, Hibernate ORM, Jakarta Persistence, native API, EntityManager API; что именно входит в Hibernate Core.
- **H01 — Общая архитектура.** boot-time и runtime; конфигурация, фабрики, сессия, persistence context, persister, event system, JDBC layer.
- **H02 — Bootstrap.** `StandardServiceRegistry`, `MetadataSources`, `MetadataBuilder`, `Metadata`, `SessionFactory`; кто и когда создаёт инфраструктуру.
- **H03 — Service Registry и интеграции.** сервисы, strategy selectors, dialect resolution, connection provider, registry lifecycle.

## Фаза B. Mapping и метаданные

- **H04 — Mapping model.** Разница между Java class, mapping metadata, relational model и runtime entity state.
- **H05 — Annotation binding.** `@Entity`, `@Table`, `@Id`, `@Column`, access type, field/property access; как аннотации превращаются в metadata.
- **H06 — Identifier generation.** assigned, identity, sequence, table generators; почему генератор ID влияет на момент INSERT.
- **H07 — Type system.** Java type, JDBC type, basic type, converters, enum, date/time, UUID, nullability и SQL type.
- **H08 — Naming и schema.** implicit/physical naming, schema/catalog, quoting, schema validation/generation.

## Фаза C. Runtime и жизненный цикл сущности

- **H09 — Session и SessionFactory.** `SessionFactory` vs `Session`, `EntityManagerFactory` vs `EntityManager`, scope и thread-safety.
- **H10 — Persistence Context.** identity map, `EntityKey`, `EntityEntry`, first-level cache, snapshots и uniqueness of managed instance.
- **H11 — Entity states.** transient, managed, detached, removed; реальные переходы и API.
- **H12 — CRUD API.** `persist`, `find`, `getReference`, `merge`, `remove`, `refresh`, `detach`, `clear`, `contains`; смысл и отличия методов.
- **H13 — Hydration.** как ResultSet превращается в entity state, роль persister/loader/result processing.
- **H14 — Insert и generated values.** action queue, insert actions, generated identifiers, возвращаемые значения.

## Фаза D. Flush, изменения и согласованность

- **H15 — Dirty checking.** snapshots, сравнение state, dirty properties, loaded state, bytecode-enhanced dirty tracking.
- **H16 — Flush.** flush triggers, flush modes, action queue, ordering, batching, почему flush не равен commit.
- **H17 — Update/Delete.** entity persister, SQL generation/execution, dynamic update, row counts и stale state.
- **H18 — Optimistic locking.** `@Version`, version increment, stale update, optimistic lock exceptions; отдельно от PostgreSQL MVCC.
- **H19 — Pessimistic locking.** lock modes, SQL locks и роль СУБД.
- **H20 — Transactions и JDBC coordination.** resource-local/JTA на концептуальном уровне, transaction coordinator, connection handling, exception conversion.

## Фаза E. Связи и загрузка графа объектов

- **H21 — Ассоциации.** `@ManyToOne`, `@OneToOne`, `@OneToMany`, `@ManyToMany`; owning/inverse side, FK и join table.
- **H22 — Cascades и orphan removal.** JPA cascade types, Hibernate cascade processing, remove semantics.
- **H23 — Lazy loading и proxies.** proxies, bytecode enhancement, persistent collections, initialization, detached access.
- **H24 — Fetching.** LAZY/EAGER, join fetch, entity graphs, batch/subselect fetching, N+1 и измерение SQL.

## Фаза F. Запросы и производительность

- **H25 — HQL/JPQL pipeline.** parse → semantic model/SQM → SQL AST → JDBC operation; отличия HQL, JPQL и native SQL.
- **H26 — Criteria и native queries.** типизированное построение запросов, result mapping, pagination.
- **H27 — Batching и JDBC execution.** statement batching, parameter binding, result extraction, ordering constraints.
- **H28 — Caching.** first-level cache, second-level cache, query cache; invalidation/regions/provider.

## Фаза G. Модель и расширения

- **H29 — Embeddable/value mapping.** `@Embeddable`, `@Embedded`, collections of values, converters.
- **H30 — Inheritance.** стратегии inheritance и SQL consequences.
- **H31 — Callbacks, listeners, interceptors, events.** lifecycle callbacks и Hibernate event system.
- **H32 — Bytecode enhancement.** lazy attributes, dirty tracking, limitations.
- **H33 — Advanced APIs.** `StatelessSession`, filters, multi-tenancy и выборочные расширения.
- **H34 — Testing, diagnostics, internals.** SQL logging, statistics, debugger/source navigation, performance testing.
- **H35 — API и annotation reference.** сводная карта важных методов Session/EntityManager и mapping-аннотаций; спецификация vs Hibernate-specific.
- **H36 — Capstone source trace.** проследить find → hydrate → manage → mutate → flush → SQL → transaction end в исходниках 7.4.17.Final.

## Фаза H. После ядра Hibernate

- **JPA-1 — Jakarta Persistence 3.2.** спецификация, portability, стандартные API и отличие от Hibernate-specific API.
- **SPR-1 — Spring ORM / transaction integration.** как Spring управляет EntityManager/Session и транзакциями.
- **SPR-2 — Spring Data JPA.** repository abstraction, query derivation, projections, specifications; что скрывает и чего не заменяет.
- **FINAL — Сквозная архитектурная задача.** разобрать реальный сервис: бизнес-вызов → Spring → JPA/Hibernate → JDBC → PostgreSQL.

## Что не является отдельной фазой повторения

PostgreSQL, JDBC, JDBC transactions, MVCC, HikariCP и JdbcTemplate считаются пройденными. Они возвращаются только как нижние уровни, когда нужно объяснить поведение Hibernate.
