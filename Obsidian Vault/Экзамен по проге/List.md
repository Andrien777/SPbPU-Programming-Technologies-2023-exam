#на3 
List - интерфейс, наследующий интерфейс **Collection**. Упорядоченная индексированная коллекция.
Основные методы:
* get(int) - доступ по индексу([] не работают)
* add(int, E), add(E) - добавление
* set(int, E) - замена
* indexOf(E)
* lastIndexOf(E)
* remove(int), remove(E)
* size()
* sort(Comparator)
* listIterator(int) - ListIterator на элемент
* .......
Возможны изменяемые и неизменяемые реализации
 factory methods: List.of(E...), List.copyOf(Collection\<? extends E>) - возвращают immutable list. 

Реализации:
* Скелетальные
	* AbstractList: add, get, set, remove, size
	* AbstractSequentialList: listIterator
* Полные
	* [[ArrayList, LinkedList#ArrayList|ArrayList]]
	* [[ArrayList, LinkedList#LinkedList|LinkedList]]

Пример:
```java
List<Integer> list = new ArrayList<>();
list.add(1);
list.add(2);
list.add(0);
System.out.println(list.get(0)); //1
list.remove(0);
System.out.println(list.size()); //2
```