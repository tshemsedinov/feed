# Timur Shemsedinov - Feed Archive - 2024

> See more: ...[2025](./README.md), [2024](./2024.md), [2023](./2023.md)...

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
