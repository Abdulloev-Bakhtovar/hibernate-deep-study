# Карта архитектуры Hibernate — ориентир, не готовый конспект

Эта карта нужна как навигация. Детали заполняются по мере прохождения уроков и сверяются с исходниками Hibernate 7.4.17.Final.

```text
Application code
    |
    v
Jakarta Persistence API / Hibernate Native API
    |       EntityManager / Session
    v
SessionFactory / EntityManagerFactory
    |
    +--> Bootstrap / ServiceRegistry / Metadata
    |
    v
Session / persistence context
    |
    +--> identity map / EntityKey / EntityEntry / snapshots
    +--> entity lifecycle / events / action queue
    +--> proxies / persistent collections
    |
    v
Load & flush processing
    |
    +--> entity persisters / loaders / mapping model
    +--> dirty checking / cascades / lock handling
    +--> HQL/JPQL: SQM -> SQL AST -> JDBC operations
    |
    v
Dialect / JDBC coordinator / JdbcServices
    |
    v
JDBC Driver
    |
    v
PostgreSQL
```

## Обязательные разграничения

- `EntityManager` — API Jakarta Persistence; `Session` — native Hibernate API, при этом Hibernate `Session` реализует/связан с контрактом EntityManager в ORM 7.
- `SessionFactory`/`EntityManagerFactory` — долгоживущая фабрика; `Session`/`EntityManager` — короткоживущий unit of work/persistence context, обычно не потокобезопасный.
- Mapping metadata — описание того, как Java-модель связана с реляционной моделью; runtime state — состояние конкретного объекта.
- Persistence Context — не то же самое, что second-level cache.
- Flush — синхронизация изменений persistence context с БД внутри транзакции; commit — фиксация транзакции.
- Hibernate optimistic locking (`@Version`) — не то же самое, что PostgreSQL MVCC (`xmin`/`xmax`).
- Hibernate не отменяет SQL/JDBC; он организует ORM-модель и координирует выполнение SQL через JDBC.

Не считать эту схему достаточным изучением. Каждый блок должен быть раскрыт на конкретных классах и методах версии 7.4.17.Final.
