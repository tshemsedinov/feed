# Timur Shemsedinov - Feed Archive - 2025

> See more: ...[2025](./README.md), [2024](./2024.md), [2023](./2023.md)...

## Coding with AI: Cursor 2025-08-05

Вчера проводил лайвкодинг с Cursor 1.3.9 (claude-4-sonet, claude-3.5-sonet, gpt-4.1, o3, gemini-2.5-pro) для студентов курса по паттернам, Node.js и асинхронности. Показал, как правильно формулировать задачу для ИИ — воспринимать его как исполнителя, а не как волшебную коробку, которая все делает за вас. Больше часа писал техническое задание, а затем ИИ очень быстро все реализовал — но все идеи уже были в ТЗ. Я предоставил примеры кода из своих предыдущих разработок, описание задачи заняло 71 строку:
https://github.com/metarhia/metautil/blob/gsid-ai/lib/TASKS.md

После этого, с небольшими доработками в течение 10–15 минут, он сгенерировал вот эти 43 строки кода:
https://github.com/metarhia/metautil/blob/gsid-ai/lib/gsid.js а также много вспомогательного кода для анализа результатов, отчета по производительности и оптимизации, который я добавил в конец файла TASKS_md.

Некоторые материалы я публикую здесь, другие будут доступны только студентам. Скоро запишу видео со сравнением — что получается, если воспринимать ИИ как ассистента, и что выходит, когда человек не понимает задачу и не умеет управлять ИИ.
## Coding with AI: Cursor 2025-08-02

🚀 Together, these technologies form the infrastructure for local-first applications:

- PWA (Progressive Web App)
  > Web apps with UX close to native: offline mode, installation, fast loading. Solve issues with poor connectivity and slow networks by combining the strengths of web and native applications.
- CRDT (Conflict-Free Replicated Data Types)
  > Data structures for automatic conflict resolution in distributed systems. Solve synchronization and concurrent editing problems, enabling offline-first applications without data loss or conflicts.
- CAS Containers (Compare-And-Swap)
  > Atomic concurrency mechanism holding entire database record protected by hashes or versions. Solve race conditions and concurrent modification conflicts, ensure data consistency, and enable optimistic concurrency control in distributed databases.
- IndexedDB (browser built-in database)
  > Client-side database API for transactional storage of structured data in browsers. Solves offline persistence, local querying, caching, and building b-tree indexes.
- OPFS (Origin Private File System)
  > Secure, high-performance file system accessible only by web applications within their origin. Solves large file storage issues and enables high-speed file operations on the web.
- Blockchain (without mining)
  > Distributed, reliable ledger for decentralized databases and immutable history. Solves data integrity, immutability, transparency, and trust issues.
- JavaScript Smart Contracts
  > Business logic executed in JavaScript within decentralized environments. Solves automation and trust issues related to data changes, ensures automatic enforcement of agreements, and secure code execution.
- WebSocket
  > Protocol for real-time, two-way data exchange over a single TCP connection. Solves latency issues and supports interactive near-real-time applications.
- WebRTC (Web Real-Time Communication)
  > Protocol for real-time streaming of multimedia and peer-to-peer data exchange. Solves issues of direct real-time communication, low latency, and decentralization without intermediary servers.
- Metaschema
  > Declarative schema language for modeling, validation, and data synchronization. Solves problems of data inconsistency, schema evolution and migration, simplifies metadata definition, and reduces complexity when working with structured data.

## PWA for offline-first 2025-07-31

Features:
- Single WebSocket connection shared across tabs
- Can be installed as a native app
- Works without internet connection
- Background caching
- Automatic reconnection
- HTTPS headers and CORS support

Link: https://github.com/HowProgrammingWorks/PWA

## AI in Engineering is a problem 2025-07-28

Главная проблема AI в программировании в том, что люди хотят, чтобы AI за них писал и был им синьором, а они ему помогали как джуны. А нужно воспринимать AI как джуна, чтобы он помогал вам, как синьору.

## How to create own framework 2025-03-04

💡 Как сделать новый популярный фреймворк:
1. Взять один случайный паттерн
2. Дать ему неузнаваемое название
3. Сделать презентацию, пообещав всем, что это и есть решение всех проблем

## Tooling vs Domain 2025-03-02

Почему так получается, что программисты все время решают проблемы инструментов, нагрузок и масштабирования, фронтенда и интерфейсов, микро оптимизации, но вообще не обсуждают проектирование предметной области, выразительность модели, когнитивная нагрузка?

- Это технологический фетишизм
- Никогда не видел бизнес-логики только CRUD везде
- Это плохой контакт с бизнесом
- Предметная область настолько разная, что мы не знаем как об этом говорить
- С предметной областью нет проблем
- Отстань, мы просто хотим писать код, закрывать ишью

👉 https://t.me/metarhia/1793

## Software Structure & Architecture 2025-02-28

New course structure

- Layered (onion), DDD, Clean architecture
- App structure, Modularity, DI, unittesting
- DTOs, models, race conditions
- Hexagonal Architecture, ports and adapters architecture
- Clustering, Parallel, Distributed systems, CAP, ACID, BASE, Locking, CQRS
- Actor Model
- Databases, data modeling
- Domain Specific Languages: DSL, AST, LISP
- Command, QueryObject, CQS, CQRS, EventSourcing
- Messaging: MQ, Pub/Sub, Pull
- System integration and topology: API, bus, brocker, MQ
- Communication styles: data, call, event, log sync, p2p, blockchain
- Feature-Sliced Design
- Architecture for Web: DDD for Frontend and Backend
- Pipeline architecture
- SOA: web services, microservices, serverless
- Data warehouses and DBMS: relational, noSQL, columnar, key-value
- API Design
- Corporate integration buses (exchange with external subsystems)
- Task and resource schedulers
- Testing, quality assessments, continuous integration
- Infrastructure, deployment, update, migration, reengineering
- Balancing, replication, sharding, resharding, backups and recovery
- Security, authorization, authentication, application firewall
- Application and system logging, incident investigation
- Analysis and reengineering of business processes

👉 https://github.com/HowProgrammingWorks/Index/blob/master/Courses/Architecture-2025.md

## Contracts: naming, clear semantics, LoD 2025-02-26

Признак хорошо спроектированного контракта (будь то интерфейс, сигнатура, абстрактный класс, фасад, тип, API...) — это когда:
- Понятно, как использовать, не заглядывая в исходники. Достаточно имен и, в крайнем случае, тестов или примеров.
- Не требует трассировки вызовов в реализации контракта. Всё очевидно на уровне интерфейса.
- Ошибки локализуются в 1 шаг, без анализа длинных цепочек вызовов.
- Следует LoD (Law of Demeter) и принципу "Do not talk to strangers", ограничивая ненужные зависимости.
- Использует осмысленное именование, которое отражает суть и минимизирует когнитивную нагрузку.

## Communication styles 2025-02-24

Про взаимодействие клиента и сервера разработчики привыкли думать в терминах конкретного протокола (websocket, grpc, http api, sse), но в первую очередь нужно выбирать стиль взаимодействия, а потом уже транспортный протокол и формат передачи данных. Вот эти стили взаимодействия:

- REST/Resources – объекты взаимодействия это ресурсы с четкой идентификацией изменяемые через CRUD-операции. Плюсы: явная адресация, идемпотентность, простое масштабирование. Минусы: плохо подходит для интерактивных и реактивных сценариев, игр, чатов, соцсетей, обновления по инициативе сервера.
- RPC/Calls – императивный подход, ориентированный на выполнение удаленных процедур и контрактное взаимодействие. Минусы: чувствительность к сетевым задержкам и версионности API. Плюсы: надежность, простота и естественность для мышления программиста.
- Events/Messages – асинхронная модель, взаимодействие строится вокруг событий и уведомлений, а не запроса-ответа. Позволяет легко масштабироваться, но и легко сломать данные, требует продуманного механизма последовательности событий и согласованности данных в условиях высокой нагрузки.
- Shared Database — Все участники взаимодействия обращаются к общей базе данных. Такой стиль переносит всю логику на клиент и упрощает интеграцию, но вместе с тем создает узкое место (SPOF) и плохо масштабируется, годится для систем с низкой интенсивностью взаимодействия, корпоративных приложений.
- Simple data sync (без разрешения конфликтов) – Передачи данных без сложных механизмов консистентности, оптимистическое сохранение, кто последний тот и прав. Хорошо работает в однонаправленных потоках синхронизации, системах с нестрогими требованиями к актуальности, однопользовательских системах.
- Operation log sync (с разрешением конфликтов) – Репликация через журнал операций, позволяющая автоматически разрешать конфликты и обеспечивать согласованность в распределенных системах. Требует строгого контроля порядка выполнения команд, использует CRDT и Operational transformation.
- Peer-to-Peer — Модель без централизованного сервера, где узлы взаимодействуют напрямую, реплицируя состояние по мере необходимости. Позволяет строить отказоустойчивые сети, но требует механики согласования состояния состояния, используется в blockchain.

## Про оптимизацию и Мурыча

> — Нужна ли оптимизация JavaScript обычному разработчику?  
> — Чем лучше будут оптимизированы библиотеки и фреймворки,  
>   тем меньше нужно залазить в оптимизацию прикладным программистам.

Кто-то думает, что это важно и интересно, другие считают, что это все фетишизм и карго культ, но в действительности все гораздо сложнее.
1. Есть продуктовые разработчики, их нельзя пускать к оптимизации, их задача эффективно решать задачи предметной области. Но у них есть соблазн и непреодолимое желание что-то поизмерять и пооптимизировать, потому, что их уже тошнит от монотонной работы... формочки, модельки и апишки. Есть ощущение, что ты мнешь дерьмо в ступе и далек от настоящего программирования. Хоть это не так, нужно вникать в предметную область, которая не так проста, вот только не хочется...
2. Есть специальные люди, вот как Мурыч, которые с утра до вечера только и занимаются оптимизацией, да... как основной профессией. Это не так просто, как кажется прикладным программистам, невозможно просто повторить операцию 10 млн раз и сравнить несколько ее реализаций, тут очень просто измерить совсем не то, что вы хотели измерить, нужно иметь большой опыт именно измерений и хорошо знать устройство виртуальной машины.
3. Есть системные программисты, которые пишут платформы, библиотеки и фреймворки, они бы хотели оптимизировать свой код и именно им это действительно нужно, но в большинстве случаев они тоже гонятся за популярностью своего продукта, и на декомпиляцию, дебаг и профайлинг времени у них мало.
4. Так вот, профессиональные оптимизаторы вполне могут подсказать им основные типовые шаблоны эффективного кода и они даже поймут многое, потому, что часто умеют опыт си и ассемблера, ну в основном понимают, так даже от понимания низкоуровневого языка, системный код становится быстрее в разы, потому, что человек может себе в общих чертах представить оптимизации, но не про все знает.
5. В прикладном коде хочется писать более понятно и надежно, что не всегда совпадает с оптимизациями. Ну часто и совпадает, но не всегда. Если их немного обучить писать оптимально под V8, добавить автоматическую проверку оптимизаций линтером, паттерны, ревью кода... то можно меньше заморачиваться оптимизацией на прикладном уровне.
6. Прикладным прогпраммистам нужно больше заниматься на семантикой, надёжностью и поддерживаемостью кода, но немного простых правил оптимизации и им тоже можно внушить. Бессмысленно прикладным программистам самим писать тесты производительности, исследовать поведение виртуальной машины, дезасемблировать код, для того, чтобы вникнуть, нужно лет 5. Но вот не писать примеси, не делать optional полей и не использовать деструктуризацию массива, не использовать юнион тайпы для классов и структур - это важно и нужно.

## Interview-oriented Knowledge 2025-01-17

- Нарешаются литкода для собесов, а потом, на реальном проекте переменную нормально назвать не могут,
- Очень любят книжку с кабанчиком, но деплоят по FTP,
- За TypeScript могут глаза выцарапать в интернетах, но `any` и юнионтайпы на каждом шагу,
- Запишут в резюме кучу фреймворков, но а потом из npm код ставят не прочитав исходника,
- Расскажут на собесе про паттерны, а потом пишут: `if (enabled === true)...`
- Полгода пилили микросервисы, но про coupling и cohesion нет, не слышали,
- На ревью кода гнобили джуна за необработанную ошибку, а в проде процесс запущен через `forever`...

> See more: ...[2025](./README.md), [2024](./2024.md), [2023](./2023.md)...
