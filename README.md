# Timur Shemsedinov - Feed Archive - 2026

> See more: ...[2026](./README.md), [2025](./2025.md), [2024](./2024.md), [2023](./2023.md)...

## Programming Knowledge: 2026-04-16

Вот собрал тут что важно по хардскилам, вместо ваших алгоритмов, литкода, высоконагруженных кабанчиков и карго-культа микрооптимизации:

- Data structures (just how to use)
- Type systems: nominal, structural, variance...
- Modularity system (in your language)
- Polymorphism (Ad-hoc, Subtype, Parametric, etc...)
- Structural composition, aggregation, delegation
- Functional composition, pure functions
- Abstraction layers separation
- Dispatch and Dynamic dispatch
- Referential transparency
- Law of Demeter
- Abstract data types (ADT)
- Hidden and explicit state
- Lazy evaluation
- Declarative vs imperative style
- Recursion versus loops
- Generics (generic programming)
- Separation of concerns
- Isolation, interfaces, architectural boundaries
- Dependency injection and Inversion of control
- Coupling and cohesion
- Mutable vs immutable data
- Idempotent operations
- Naming conventions
- Error handling
- Refactoring, code review process
- Tests (unittesting, coverage, end-to-end...)
- Multiparadigm programming
- Metaprogramming (codegeneration and dynamic)
- Platform-agnostic, framework-agnostic approach
- Domain-Specific Language (DSL), Interpreter, AST
- Contract programming
- Concurrency and Asynchronous programming
- Separation of system and applied code
- Language and semantics
- AI-assisted engineering

Но все это тоже должно занимать в голове не более 30% от развития инженера, as of 2026. Про 70% напишу еще чуть позже
Repo: https://github.com/tshemsedinov/Programming-Knowledge

## Ralph Loop: 2026-03-15

AI loop (например Ralph) - это порочный круг, на каждой операции ниоткуда не добавляются новых знаний. Нужно стараться, чтоб AI выдавал результат за один раз. А на каждый следующий цикл можно заходить, если есть новые вводные, иначе все это деградирует и сжигает деньги и ваше время. Вот что я хотел на самом деле написать в том посте, который неправильно поняли и который я удалил, хоть я не имею обыкновения удалять посты. Но просто хочу высказаться более точно. Если нужен оригинальный текст, он сохранен тут: https://github.com/tshemsedinov/feed?tab=readme-ov-file#ai-infinite-loop-code-review--tasks--coding-2026-03-12 

Проблема не в самом цикле, а в том, что вы не хотите тратить внимание и добавлять новой информации на каждом новом шаге. Модель начинает усиливать собственные ошибки и шум.

Проблема - это пустой цикл.

Если на каждой итерации не появляются новые вводные, принятие решений, ограничения и требования, новый контекст, то система просто пережевывает собственный вывод.

Поэтому:
- первый проход должен стремиться дать максимально полный результат
- каждый следующий проход должен добавлять обратную связь
- если новых данных нет - итерация бессмысленна, ошибки закрепляются

## AI infinite loop: Code review + Tasks + Coding 2026-03-12

Ревью кода и постановка ТЗ занимает много времени в программировании с AI и люди, естественно, пытаются переложить эту задачу тоже на AI. Пусть агенты друг-другу ТЗ пишут, друг-друга дрессируют и ревью делают. Так можно дойти и до кнопки "Сделай все хорошо", которая запускает бесконечный цикл. У вас не выйдет не тратить внимания на проект.

AI про ваши потребности не занет и мысли не читает. Идеи, приоритеты, контекст, критерии качества и продуктовые компромиссы он сам не определит. AI хорошо пишет только то, что уже много раз кем-то писалось. Если убрать из процесса человеческое внимание, вы не ускорите проект - вы просто зациклите галюцинирование.

На проект все равно придется тратить внимание. Вопрос не в том, как убрать человека из контура, а в том, куда именно направить внимание и в какой форме его вписать в жизненный цикл разработки, чтобы получить максимальную отдачу. Например, в виде DSL-языков, в форме md-файлов или json-файлов, блок-схем, в виде ревью или архитектурных документов.

- Не заменять ревью, а удешевлять его через стандарты, скилы, субагентов, экономию контекста
- Не строить зацикленные цепочки агентов, а ограничивать зоны их ответственности
- Не пытаться автоматизировать мышление целиком, а освобождать внимание человека от рутины
- Не держать требования в текстовой форме, а выносить логику в строгие синтаксисы и контракты
- Не надеяться на память чата, а собирать контекст в версионируемые артефакты, схемы и спецификации

## JavaScript Standard Library and Web API 2026-01-02

У JavaScript две проблемы: отсутствие развитой стандартной библиотеки, как у C++, Java, .Net и очень развитое WebAPI, которого почти никто не знает и знать не хочет. И вместо первого и вместо второго используют всякую мерзость из npm. 

Стандартная библиотека должна давать нам: струкутры данных (linked list, trees, stack, queue, deque...), контейнерные типы (result, either, maybe...), алгоритмы (hasing, search, conditional probabilities...), утилиты асинхронного и параллельного программирования (semaphore, mutex...), машинно-ориентированные типы: f32, f64, i8, u8..., i128, u128 (у нас только часть их есть и то только внутри typed arrays) и много еще чего.

Web API: OPFS, WebCrypto, AbortController, Web Locks, Web Streams, BroadcastChannel, Atomics, Scheduling, Weak collections, WebTransport, Workers, View Transitions, по работе с датами и юникодом, блютузом и рендерингом... там их много пейдждаунов

> See more: ...[2026](./README.md), [2025](./2025.md), [2024](./2024.md), [2023](./2023.md)...
