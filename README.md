## Consistent return 2023-07-05

- Примериы consistent return как для возврата значений через return, так и для callback: https://github.com/HowProgrammingWorks/ConsistentReturn/tree/main/JavaScript
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
