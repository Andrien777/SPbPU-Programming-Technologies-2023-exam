#на3 
Map - интерфейс, **HE** наследующий **Collection**. Ассоциативный неупорядоченный массив, хранит пары ключ-значение. Ключи уникальны.
static вложенный интерфейс **Entry** реализует доступ к одной конкретной записи.

Возможности Entry:
* getKey()
* getValue()
* setValue()

Основные возможности Map:
* entrySet()
* get(K), getOrDefault(K, V)
* put(K, V), putIfAbsent(K, V)
* remove(K), remove(K V)
* keySet()

Возможны mutable и immutable
 factory methods: Map.of(K, V, K, V...), Map.ofEntries(Map.Entry\<? extends K,? extends V>...), Map.copyOf(Map\<? extends K, ? extends V>) возвращают immutable

Реализации:
* Скелетальные:
	* AbstractMap - на базе entrySet
* Полные 
	* [[HashMap, TreeMap#HashMap|HashMap]]
	* [[HashMap, TreeMap#TreeMap|TreeMap]]
	* EnumMap

Пример:
```java
Map<String, Integer> map = new HashMap<>();
map.put("One", 1);
map.put("Two", 2);
System.out.println(map.get("One")); //1
map.put("One", 3);
System.out.println(map.get("One")); //3
System.out.println(map.get("Three")); //null
```