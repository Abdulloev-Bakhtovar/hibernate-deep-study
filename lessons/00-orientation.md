# H00 — Ориентация в Hibernate и карта архитектуры

- Статус: `NOT_STARTED`.
- Предпосылки: H00-PRE.
- Версия: Hibernate ORM `7.4.17.Final`.

## Цели

После урока ученик должен различать:
- ORM как подход и Hibernate ORM как реализацию;
- Jakarta Persistence как спецификацию/API и Hibernate как провайдера/реализацию;
- native Hibernate API (`Session`, `SessionFactory`) и JPA API (`EntityManager`, `EntityManagerFactory`);
- boot-time и runtime;
- что Hibernate добавляет поверх JDBC, не подменяя сам JDBC.

## Содержание

Агент должен объяснить только верхний архитектурный уровень. Не уходить пока в детали Persistence Context, dirty checking, SQL AST или внутренние классы.

## Первая практика

Ученик должен самостоятельно изобразить и объяснить верхнеуровневую цепочку:

`Application → EntityManager/Session → SessionFactory → mapping/runtime services → JDBC → PostgreSQL`.

Ученик должен обозначить, какие объекты долгоживущие, а какие относятся к одной единице работы. Детальные роли пока не проверяются — они будут изучаться в следующих уроках.

## Контрольные вопросы

1. Почему Hibernate — не замена JDBC?
2. Чем Jakarta Persistence отличается от Hibernate ORM?
3. Почему `SessionFactory` и `Session` не должны иметь одинаковый жизненный цикл?

## Критерии DONE

- Ученик своими словами объяснил три различия выше.
- Самостоятельно нарисовал верхнеуровневую цепочку.
- Не смешивает JPA API и Hibernate-specific API.
- Результат сохранён в карточке урока и state-файлах.
