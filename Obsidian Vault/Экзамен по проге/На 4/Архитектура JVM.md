#на4
JVM - виртуальная машина - "компьютер", состоящий из "процессора" и памяти. Процессов работает с собственным языком - [[JVM байт-код|байт-кодом]].
JVM имеет [[Стеки, очереди#Стек|стековую]] архитектуру: все операнды хранятся на стеке, количество регистров стремится к минимуму, многие операции операндов не имеют, работают только на стеке.

Программы состоят из файлов .class специфицированного формата. В одном файле хранится только один класс.

JVM:
* знает, что такое класс
* не понимает [[Generics|дженерики]] и [[Локальные классы, Анонимные классы#Локальные классы|локальные классы]]
* понимает только top-level и [[nested classes vs inner classes|nested классы]]

Структура .class
* сигнатура - id файла
* версия 
* пул констант, хранит константы, имена методов и полей, индексирован
* флаги доступа - метаданные класса/интерфейса
* this class - ссылка на запись в пуле констант
* superclass - ссылка на запись в пуле констант
* реализуемые интерфейсы - набор ссылок на записи в пуле констант
* поля - количество полей и поля. В каждом поле определены тип и имя (ссылкой на запись в пуле констант)
* методы - количество и список реализаций на [[JVM байт-код|байт-коде]]
* атрибуты

Реализация видов классов:
* top-level - напрямую
* [[nested classes vs inner classes|nested]] - напрямую с декорированием имени: Outer\$Nested
* [[nested classes vs inner classes|inner]] - содержит неявную ссылку на внешний класс
* [[Локальные классы, Анонимные классы|локальные и анонимные]] - содержат ссылку на контекст

Устройство памяти:
* регистр PC - счетчик команд
* [[JVM стек]]
* JVM heap - куча, место хранения ссылочных типов данных, общая на все потоки, реализована сборка мусора
* JVM method area - хранит исполнимые коды методов, доступ общий для всех потоков
* JVM constant pool - пул констант, свой для каждого класса, хранит константы, имена методов и полей, индексирован

В дженериках параметр типа стирается, вместо него подставляется Object или граничный класс при указании такового