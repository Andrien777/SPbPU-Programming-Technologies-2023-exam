#на3 
Set - интерфейс, наследующий **Collection**. Неупорядоченное множество, не содержащее равных элементов.
Основные методы:
* add(E)
* contains(E)
* remove(E)
* .........
Возможны mutable и immutable
 factory methods: Set.of(E...), Set.copyOf(Collection\<? extends E>) возвращают immutable

Реализации:
* Скелетальная
	* AbstractSet
* Полные
	* [[HashSet, TreeSet#HashSet|HashSet]]
	* [[HashSet, TreeSet#TreeSet|TreeSet]]
	* [[EnumSet]]

Пример:
```java
Set<Integer> set = new HashSet<>();
set.add(0);
set.add(1);
System.out.println(set.size()); //2
set.add(0);
System.out.println(set.size()); //2
```