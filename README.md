## Microservices and Complexity 2024-09-24

🏛️ [Проблема сложности](https://x.com/tshemsedinov/status/1838452655242514609), которую решают микросервисы, на самом деле решается проектированием структуры кода на среднем уровне, т.е. люди от функций и классов хотят перескочить сразу к архитектуре, минуя модули, слои, подсистемы. Если код хорошо структурирован на среднем уровне благодаря:

- системам модульности,
- внедрению зависимостей и инверсии управления,
- архитектурным границам и слоям,
- декомпозиции абстракций,
- separation of concerns,
- information expert,
- контрактному программированию,
- управлению, сокрытию и изоляции сложности,
- разделению прикладного и системного кода,

то такое приложение можно в течении нескольких часов собрать в 2, 3, 5, 105 инстансов, заменив взаимодействие между их структурными компонентами на RPC и трансляцию событий. Так, что модули и подсистемы знать не будут, что они запущены не в одном процессе. А если код «рыхлый», то его и микросервисом не изолировать, у такого сервиса будет большой внешний трафик, потому, что зацепление на чужие данные и чужую логику высоки. Так что, «распиливание» это только распиливание бюджета команд и бюджета на инфраструктуру. Обойти вопрос хаоса на среднем уровне при помощи чуда не выйдет. Чтобы построить Application архитектуру, нужна качественная структура, а чтобы перейти к Solution и Enterprise архитектуре, нужна качественная Application архитектура. Попытки перескочить от функции, цикла и массива к Solution архитектуре приводят к появлению монстров типа облачных функций, микролитов, моносервисов и скоро мы увидим Variable as a Service, а потом гору этих абстракций, вываленных на уровень Solution, не сгруппированных и не изолированных в структурные единицы управления сложностью. Чуда не будет, ни кто не решит за нас вопрос перехода от отдельного кирпича к небоскребу, нужны промежуточные структурные единицы.

👉 Patterns 2024 Training: https://github.com/HowProgrammingWorks/Index/blob/master/Courses/Patterns-2024-ru.md

## The Law of Demeter 2024-08-06

🙊 The Law of Demeter (LoD): Don’t talk to strangers

If you see something like this:
- 👉 connection.parent.service.storage.db.saveRecord
- 👉 this.action.scenario.bot.telegram.sendMessage
- 👉 service.find('logger').kind('error').stream.write

You have technical debt! It's time to plan refactoring.
Each entity (unit/instance) should have only limited knowledge about others (only "closely" related to the current one).
Each entity should only talk to its friends (immediate friends): don’t talk to strangers!

Вut don't do it in a panic and do not mix refactoring with other issues (like new features implementation).
Just note that and plan resource allocation.

## TypeScript union-тайпы 2024-08-05

Почему нужно избегать union-тайпов?

1. Каждый раз, когда юнион куда-то приходит аргументом, нужно делать if, чтобы понимать, как с ним работать, кроме случая, когда все классы/типы, входящие в юнион имплементируют один и тот же интерфейс и нас интересует обращение именно через этот интерфейс, зачем тогда юнион, используйте этот интерфейс вместо него, ну если в юнион не входит undefined, null, unknown и т.д.

2. Юнионы приводят к мегаморфной форме обращения к объектам в V8, и это замедляет код, не сметртельно, но это неприятно и проще всего всего забыть их. Но для чего же они тогда вообще нужны? Для совместимости с JS, если в нем можно передать что-угодно аргуметом, то это нужно меть возможность как-то выразить. Это не значит, что это хорошо и так нужно писать кода, это добавили как возможность, а не как обязанность )

3. Это часто ведет к нарушению SOLID:SRP (принципа единственной отвественности), потому, что как может метод, например, получать сокеты или таймеры на выбор и делать разные вещи в зависимости от этого, это же маразм, нарушает SOLID:LSP (принцип подстановки), иногда нарушает GRASP:InformationExpert, явно повышает Coupling.

Вместо этого нужно всегда использовать маленькие интерфейсы, заточенные под узкую задачу, помним про SOLID:ISP (принцип разделения интерфейсов) и могут быть optional аргументы, для этого не нужно делать union с null.

## Patterns for JavaScript & Node.js 2024-07-22

Here is special repo for course and links about rethinking GRASP, SOLID, GoF patterns, for Frontend (browsers) & Backend (node.js, other runtimes) development with JavaScript and TypeScript.
- Github: https://github.com/tshemsedinov/Patterns-JavaScript
- Initial Twitter article: https://x.com/tshemsedinov/status/1815304825719881808

## Promise.withResolvers 2024-07-20

Article about `Promise.withResolvers()` https://x.com/tshemsedinov/status/1814658617821307282 with examples and use cases.

## NodeJS Interview Question 2024-07-07

✨🐢 NodeJS 2024 🚀✨ Interview questions and recommendations for app and system backend developers. 
- 55 questions for Applied Node.js backend engineer
- 60 interview questions for system Node.js backend engineer
Link: https://github.com/tshemsedinov/NodeJS-Interview-Questions

## Essential Knowledge for Programmers 2024-07-06

Here's what I suggest learning and practicing.

- Github repo: https://github.com/tshemsedinov/Programming-Knowledge
- Initial Twitter article: https://x.com/tshemsedinov/status/1809633457754034433

## Async Interview Questions 2024-07-04

Asynchronous programming interview questions and recommendations for JavaScript and TypeScript developers: https://github.com/tshemsedinov/Async-Interview-Questions

## Screening 2023-11-24

💥 Увольте своих HR если они говорят вам, что нужно усилить фильтры формальными требованиями и ужесточить скрининг.  
— А кто же будет проводить скрининг?  
— Сами кандидаты. Попробуйте:  
Опубликуйте больше подробностей о проекте и вакансии, о компании и коллективе. Сделайте опросник для самостоятельного оценивания уровня кандидатов. Набросайте типовых issue, которые будут встречаться в работе. Опишите того, кто вам нужен. Кандидаты сами в состоянии оценить себя, потянут ли они. HR, в большинстве случаев, просто искажает коммуникацию между специалистами, не давая действительно важной информации проникнуть к кандидатам, а действительно стоящим кандидатам проникнуть к команде. Ни какие формальные критерии не могут быть адекватными. Не бойтесь, в конечном счете, обмануть невозможно, какой смысл кандидату врать, если все выяснится очень быстро. Да, будут сбои в такой системе, будут появляться неадекваты, но разве они не проходят формальные фильтры? А в подавляющем большинстве случаев люди способны себя оценить адекватно.

## Metarhia 2023-11-06

Куда идет Metarhia: В мире Java и C# все решают платформы и большие технологические стеки типа hibernate. Где-то они идут как зависимость, но безальтернативная, а где-то как часть платформы, но основной смысл - в них все продумано, есть решения для всего и программирование переходит на уровень прикладных задач, потому, что все системные уже решены в платформе. В мире node.js такого нет, тут десятки тысяч библиотек, которые не согласованы друг с другом, но их в принципе можно заставить работать вместе. Вот программисты и занимаются 80% времени тем, что их связывают, налаживают, оборачивают и согласовывают. То логгер отпал, то конфиг поскользнулся, то роутинг разлетелся, то валидация отпала. Все это из-за версий, прекращения поддержки библиотек, появления новых, изменения в политике библиотек, их же авторы делают под себя и свои нужды, которые меняются. Собирать заведомо несовпадающие пазлы при помощи ножниц и клея - такая себе затея, в каждый момент времени она решаема, но все рассыпается в руках, поддерживать это очень сложно. Метархия готовит инфраструктуру, в которой вам нужно будет знать минимум и настраивать минимум, даже знаний по ноде нужно будет в десятки раз меньше, чем на чистой ноде писать, не говоря уже про разные зависимости. Все писало стак, чтобы было нужно минимум документации, минимум примеров. Но забудьте про то, что вы сможете решить задачу так, как вы привыкли ее решать, для всего есть готовые решения, их минимум, но все их нужно освоить со старта, и это составляет целостный инструментарий для проектов класса "информационная система", то есть, есть база данных, есть апи и доменная логика. Таких систем самое большое количество, конечно можно делать и игры и колаборативное редактирование и стриминг и чаты и уже даже для публикации контента многое сделано, но есть основное направление платформы и она будет затачиваться под 3-4 типа приложений, их уже сейчас можно делать в 100 раз быстрее, чем на фрейворках типа nest.js, потому, что мы берем идею цельной платформы их Java и C#, но не берем весь кровавый энтерпрайз, а делаем все легковесным, даже DDD и чистая архитектура у нас реализуются максимально компактно и без оверинженеринга. Доку можно прочитать за 30 минут всю https://github.com/metarhia/Docs До конца месяца будет готов пример достаточно сложного приложения и видео-курс с разбором его разработки за один день одним человеком.

## Metarhia Documentation 2023-10-23

Технологический стек Metarhia теперь с документацией и готовится курс быстрой разработки и примеры приложений. https://github.com/metarhia/Docs

- Первый сервер приложений для Node.js с масштабированием потоками
- Поддержка изоляции выполнения между пользователями и запросами
- Автоматическая маршрутизация API-вызовов к API эндпоинтам (нет необходимости добавлять маршруты вручную)
- Тайм-ауты и очередь выполнения запросов с ограничением ожидания
- Схемы для контрактов API, авто-валидация структур данных и моделей
- Поддержка нескольких протоколов: HTTP, HTTPS, WS, WSS
- Разные стили API: RPC через AJAX и через Websocket, REST и веб-хуки
- Обновление кода и SSL сертификатов на лету, без перезагрузки процесса
- Автозагрузчик модулей и graceful shutdown с хуками start и stop
- Авто-генерация пространств имен для кода и зависимостей
- Минимум как прикладного кода, так и кода платформы, нет зависимостей
- Слоеная архитектура: api, бизнес-логика, доступ к данным, системный код
- Песочницы для улучшенной безопасности и изоляции контекстов выполнения
- Предотвращение загрязнения глобального контекста, загрязнения ссылками
- Встроенный балансировщик с перенаправлением на порты воркеров
- Кеширование в памяти для API и статических файлов
- Автозагрузка конфигов с вариантами для разного окружения
- Слой доступа к базе, совместимый с PostgreSQL, с защитой от инъекций
- Персистентные сессии с аутентификацией, группами или анонимные
- Буфферизованный лог (ленивая запись) с ротацией (хранение N дней)
- Интегрированный нативный тест раннер node.js и табличными тестами
- Утилиты для файлов: загрузка, скачивание, partial-content и потоки
- Планировщик для выполнение задач в определенное время

## Syntactic garbage 2023-10-16

🙈 Синтаксический мусор — это как синтаксический сахар, только мусор, это все, избыточное, что не способствует выразительному и хорошо читаемому синтаксису, все, что не содержит полезной информации и нужно только ради формальности, лишние абстракции, модули, прослойки, классы, декораторы и аннотации, файлы, конфиги, и все, что дублируется, копипастить, все время повторяется по шаблону. Синтаксический мусор, это то, из чего на 80% состоит шаблон приложения из интернета или тот, что вы тянете из проекта в проект.

## Beginner's call 2023-10-13

😜 Есть такой эффект, и я иногда чувствую вину за его распространение: человек только осваивает язык и платформу, но попадает на сложную лекцию о том, как все устроено внутри, о недокументированных функциях, оптимизациях, высоконагруженных и распределенных системах, многопоточности, сборке мусора, метапрограммировании, ивентлупе и т.д. и вот ему дают задачу (или он сам себе ее ставит) например: «сделать апи для получения с сервера списка городов» и тут он вспоминает про асинхронные генераторы, бекпрешер в стримах, про инверсию управления и начинается... нужно все сделать по науке, чтоб миллион пользователей пришло и что будет, если каждый 10 раз в секунду будет выкачивать список, в котором сотни тысяч записей, а может быть давайте не в JSON слать, а придумаем для этого бинарный протокол и сэкономим на кавычках и запятых, будем строки разделать байтом FF, и обязательно предусмотреть отмену получения списка и докачку, если соединение разорвалось с того же места и чтоб кеширование работало, но была возможность принудительно кеш обновлять... А если справочник меняется, то нужно вебсокетами присылать изменения, нужно придумать в каком формате, и таймаут держать в памяти, что если докачка не началась в течении 5 минут, то уже не начнется, а если соединение восстановлено, но мы подключились к другому процессу или потоку, а если сервер перегрузился нужно же... и это бесконечно, так складывание двух чисел можно защищать от влияния космических лучей... я уже не говорю про микротесты и нагрузочные тесты, которые непременно нужно нужно гонять пару часов. Ну... все это... конечно способствует освоению платформы, это интересно и через пару лет может дать полезные результаты и я не хочу отговаривать от экспериментов, но признайтесь себе, сколько будет пользователей, данных и интенсивности через год, два, три, прикиньте грубо, ну на 2 можно умножить и дать себе отчёт в действительных целях своего R&D.

## Async timeouts 2023-10-10

Тут несколько способов добавления таймаутов к асинхронному API (на примере `fetch`), конечно `fetch` поддерживает `AbortController`, но не все знают про `AbortSignal.timeout()` и есть API без такой поддержки, так что сравнить есть что. https://github.com/HowProgrammingWorks/AbortController

## WebAssembly loader 2023-08-07

Пока делал лекцию по WebAssembly для курса по Node.js с использованием Rust, C++, WAT, AssemblyScript, обнаружил, что wasm-pack имеет невменяемый и глючный загрузчик на 3 кила, вот тут загрузчик на 10 строк для ноды https://github.com/HowProgrammingWorks/WebAssembly Более универсальный вариант опубликован уже в npm, лежит тут: https://github.com/tshemsedinov/wasm-import

## Drop Nodejs 14 support 2023-08-02

🚀 Весной я сделал чеклист по портированию проектов на новые версии #NodeJS — прекращение поддержки 14.x и рекомендации по внедрение всех новых возможностей из 16.x, 18.x, 20.x — https://github.com/tshemsedinov/Drop-Nodejs14
⚡️ Сейчас уже начал готовить такой же документ по прекражению поддержки 16.x, т.е. переходу возможности, поддерживаемые в 18.x и 20.x
⚡️ Замечу, главный упор тут, не появление новых возможностей в новых версиях, а именно прекращение поддержки старых версий, которые мешали использованию новых возможностей.

## SQL templates for JavaScript 2023-07-17

Наилучший из мне известных способов вставить SQL в код на JavaScript с использованием шаблонных строк, подстановкой переменных в формате `${name}` и именованных параметров через `${'name'}` и передачей параметров в виде объекта-коллекции. Код и тесты (они же примеры вызова) тут: https://github.com/metarhia/metasql/pull/273/files
```js
const query = db.sql`
  SELECT * FROM "City"
  WHERE "cityId" < ${5} AND "name" <> 'La Haye-en-Touraine'
  ORDER BY name LIMIT 3
`;
const cityCodes = await query6.dict('name', 'cityId');
// { Alexandria: '3', Athens: '4', Paris: '1' }
```
Можете сравнить с пердыдущим примером билдера. Ленивый учит дважды: если кто учил ORM, чтобы не учить SQL, то будет учить и то и другое.

## Query builder concept 2023-07-11

Самый простой пример билдера запросов с поддержкой цепочек вызовов (чеининг) и контракта Thenable: https://github.com/HowProgrammingWorks/Thenable/blob/master/JavaScript/a-query.js
```js
const sql = await new Query('cities')
  .where({ country: 10, type: 1 })
  .order('population')
  .limit(10);
```

## Training projects 2023-07-10

Каким должен быть хороший учебный проект? Для разработчиков информационных систем или data-aware (а это большинство программистов), систем где есть базы данных, пользовательский интерфейс, сервер приложений и взаимодействие по сети, модель предметной области и бизнес-процессы. Сюда прекрасно ложится и веб и энтерпрайз. Так вот, учебный проект лучше начинать не позднее чем через полгода после начала обучения и он должен быть сложный и желательно групповой, делаться несколько лет, постепенно с усложнением, включать не менее половины из: логирование, конфигурация, аутентификация и система прав, отложенные задачи, роутинг запросов, генерация отчетов, миграции, юнит-тесты, интеграционные и системные тесты, автоматическая сборка, телеметрия и сбор статистики, потоковое вещание, очереди, балансировка или оркестрация, интеграция с другими системами, интернационализация, резервное копирование и восстановление, распределенное хранение и обработка данных, коллаборативное редактирование, парсинг, система плагинов, многопоточность или асинхронность, многоуровневое кэширование, сессии, несколько разнотипных СУБД (например postgresql и redis), кодогенерация, обработка метаданных и метапрограммирование, многослойность, изоляция (запросов, пользователей, модулей и т.д.), межпроцессное взаимодействие и удаленный вызов процедур, транзакции и блокировки, рассылка почты и прочих нотификаций.

## Consistent return 2023-07-05

- Примериы consistent return с использованием `void` как для возврата значений через `return`, так и для `callback`: https://github.com/HowProgrammingWorks/ConsistentReturn/tree/main/JavaScript
- Eslint правила и примеры: https://eslint.org/docs/latest/rules/consistent-return

## Middleware 2023-07-03

По паттерну Middleware нужно отдельно пояснить, он не только приводит нас к race condition, а точнее и к конфликтам по данным и к конфликтам по control flow, но еще и всячески усиливает зацепление (coupling) кода:
- ⚠️ **Провоцирует практику примесей** (mixins), например: res.sessionStarted = true; и потов в куче мест if res.sessionStarted или res.userName = 'idiot';
- ⚠️ **Провоцирует протекание абстракций** - когда мы залезаем во внутренности req и res и правим их состояние, а также состояние их частей, сокетов, заголовков и т.д. не через внешний интерфейс, т.е. методы, не по контракту, а патчами, обертками, в общем, таким образов, например, ws (библиотека вебсокетов) патчит http сервер и внедряется в его середину для перехвата апгрейда до вебсокетов. Очень хорошо, что так можно сделать в JavaScript, это позволяет быстро решить любую проблему, но такое решение нужно хорошо продумать, покрыть тестами, и вероятность, что оно развалится все же велика. В системном коде это еще ок, а вот в продуктовом нужно максимально снижать протекание, полностью, конечно, его вообще невозможно уничтожить, см. "Закон дырявых абстракций".
- ⚠️ **Провоцирует reference pollution** и использование шаренного состояния: ссылки на req и res расползаются по разным частям программы, например: serviceName.method(req, res, ...); или на части req и res, пример: serviceName.method(req.socket, ...); или так: outside.emit('request', req); много есть способов: const f1 = method.bind(req); или const f2 = method(req)(res); и еще сотни.
- ⚠️ **Провоцирует состояние гонки** (race condition): через использование структуры данных за пределами middleware и потом использование такой структуры внутри нескольких middleware сразу или за счет того, что ссылки на req и res попали в другие части программы и оттуда меняется их состояние уже без привязки к next, например по setTimeout кто-то сделал таймаут отправки результатов или на по приходу какого-то события из стримов req и res кто-то хеадеры пишет, а потом другой мидлвар уже не может хеадеры записать. Это только самые частые проблемы, вы разве не сталкивались, когда мидлвары переставляют местами, чтобы найти такую последовательность, чтобы оно таки запустилось, так вот это плохая практика, она только скрывает гонку, но при нагрузке она может вылезти.
- ⚠️ **Провоцирует** писать **толстые контроллеры** и **смешивать в них разные слои**, ну мы видели все, такой эндпоинт, в котором все сразу, и работа с http протоколом, и бизнес-логика и обращение к базе данных через SQL и запись кеша в redis и отправка задачи в очередь и работа с файловой системой, да что угодно, все простыней... нет, конечно, никто так писать не заставляет, просто не все в курсе, что нужно делать слои, и выделять работу с базой в репозиторий и т.д., точнее, знают многие, но мало кто может так делать.
- ⚠️ **Повышает зацепление** (code coupling) - все части кода становятся более зависимы друг от друга благодаря всему вышеописанному, и пошевелишь одно, а ломается в другом месте.

## Node.js patterns 2023-07-03

💡 Самые распространенные: паттерны проектирования для JavaScript и Node.js
- 🧩 **EventEmitter** (он же Observer), встроен в ноду, а на фронте полифил или EventTarget,
- 🧩 **Proxy** - встроен в язык, перехват обращений к объекту,
- 🧩 **Strategy** - у нас это просто Object или Map - коллекция функций, классов, прототипов, замыканий и т.д.,
- 🧩 **Facade** - упрощенный интерфейс к сложной системе, много где используется, например http2.createSecureServer скрывает от нас как TLS, так и HTTP, потоки, сессии и другие механизмы,
- 🧩 **Adapter** - обычно функция-обертка, wrapper, примеры: promisify, callbackify, или можно написать полифил fetch, использующий внутри XMLHttpRequest, это будет адаптер, скрывающий сложность, но не фасад, потому, что за фасадом скрывается не один интерфейс, а несколько или целая подсистема,
- 🧩 **Factory** - Фабрика, это паттерн, который создает экземпляры класса, но в JS фабрика может порождать экземпляры прототипов, замыканий,
- 🧩 **ChainOfResponsibility** - обычно используется его псевдо-аналог Middleware, который приводит к конкуренции за шареный стейт и так ведет нас к состоянию гонки, про оригинальный ChainOfResponsibility всем стоит почитать, чтобы перестать использовать Middleware,
- 🧩 **Decorator** - встроеный в язык, при чем в JavaScript и в TypeScript, спецификации отличаются, но суть так же, добавляет поведение без наследования, за счет метаданных,
- 🧩 **Singleton** - это у нас просто объект, для этого даже класс создавать не нужно, а глобальная уникальность экземпляра может достигаться при помощи экспорта из модуля,
- 🧩 **Revealing constructor** - открытый конструктор, например, передавая метод write в конструктор Writable через options мы можем получить Writable с переопределенным методом без наследования, так же и с передачей функции в конструктор Promise, мы так привыкли к этому, но в других языках это традиционно делается через наследование.

## Найм сломан 2023-06-28

Есть два типа людей:
1. Научился писать круды — устроился формошлепом.
2. Научился делать масштабируемые, надежные, высоконагруженные распределенные системы — устроился формошлепом.

## Что учить 2023-06-25

Если Вы учите программирование и рассчитываете работать в типичном продукте или аутсорсе, в стартапе или фрилансе, то вот на чем можно сэкономить. Но это не касается тех, кто хочет стать системным программистом и работать в технологической компании. Так вот, чтобы быстрее учиться и что скорее всего никогда не понадобится в реальном продуктовом коде:
1. Алгоритмы и задачи с литкода или кодеварс вам не нужны. Но нужен навык простого процедурного и ООПшного кода + GRASP и SOLID.
2. Всякие учебные задачи, типа todo листа, калькулятора, крестики-нолики. Нужно делать более комплексные вещи, полноценный проект.
3. Бесконечное смотрение видео тоже ни к чему не приведет, нужно получать ревью кода, желательно от наставника или от друзей.
4. Задачи на системный дизайн не нужны, Это знания, которые нужны лиду, архитектору и CTO и валидны только при закреплении на практике.
5. Микрооптимизация, типа сравнения по производительности object[key], obejct.key и Object.assign. В начале пути одна задача - понятность кода.
6. Не нужно заучивать все паттерны (GoF и еще сотню), в зависимости от языка и фреймворка вам понадобится всего 2-3 шаблона проектирования.
7. Не старайтесь изучить внутреннее устройство event loop, garbage collection, goroutine scheduler, это спрашивают на собесах, но не нужно в работе.
8. Не ведитесь на крутые темы, типа высоконагруженных, распределенных и супер-защищенных приложений, вас к ним еще долго не допустят.
9. Не зацикливайтесь на языке, язык гораздо проще тулинга, поднажмите на git, github, линтеры, ide, docker, ci и тестирование, тулы для отладки.
10. Ничто так не отвлекает от изучения программирования, как ВУЗ и не внушает ложного чувства уверенности, как ИТ-курсы от инфожуликов.
