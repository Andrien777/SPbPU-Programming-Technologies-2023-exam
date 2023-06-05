by Vusketta

>How to live in the world, where humanity tries to simplify everything, but it doesn't work at all? © В.В. Алина, 2023

*Generics (Дженерики) — это механизм обобщения кода, который появился в J2SE 5.0 (в год вашего рождения). 

Допустим начальник нашей прекрасной компании H\*\*\*\*i дал нам следующее ТЗ:
	`Написать метод, позволяющий проверить, содержит ли массив какой-то конкретный элемент`. 
Из поставленного ТЗ не очень понятно, какого типа могут быть эти _элементы_. Значит нужно поддерживать все типы.
```java
/* Любой бы написал это так (нет, не любой): */
/* T - типовой параметр */
public <T> boolean contains(T item, T[] array) {
	for(int i = 0; i < array.length; i++) {
		if(item.equals(array[i])) {
			return true;
		}
	}
	return false;
}
```
На этом моменте достаточно смышлёный ~~айтишник~~ 
Java-программист смутился. Почему нельзя сделать вот так?
```java
public boolean contains(Object item, Object[] array) {
	for(Object item : array) {
		if(item.equals(array[i])) {
			return true;
		}
	}
	return false;
}
```
Ответ довольно простой — можно.
Тогда какого $#\*@%!!! вы мне тут пытаетесь продать какие-то дженЕрики? Вы что алкаши? Да, но пьем по праздникам. 
На самом деле, причины следующие:
- Хорошая проверка типов во время компиляции.  
    Исправлять ошибки, вызванные во время компиляции, куда проще, чем ошибки, вызванные во время исполнения.
- Избавление от постоянных кастов.  
    Без дженериков:
    ```java 
    List list = new ArrayList();
    list.add("hello");
    String s = (String) list.get(0);
    ```
    С дженериками:
    ```java 
    List<String> list = new ArrayList<>();
    list.add("hello");
    String s = list.get(0);   // no cast
    ```
- Возможность реализовать _обобщённые_ алгоритмы.  
   (`contains(T item, T[] array)`).

На данный момент мы поняли, что такое дженерики и зачем они нужны, но это только начало веселого пути самурая.
Существует такое понятие, как _generic class_. Это классы, которые объявлены следующим образом: 
```java
class ClassName<T1, T2, ..., Tn> { /* ... */ }
```
Или вот типичный пример с коробкой:
```java
public class Box<T> {
    private T t; /* хранит поле типа T */
	/* метод перезаписывает это поле */
    public void set(T t) { this.t = t; }
    /* метод возвращает это поле */
    public T get() { return t; }
}

public static void main(String[] args) { 
	Box<Integer> integerBox1 = new Box<Integer>(); // OK
	Box<Integer> integerBox2 = new Box<String>(); // ???
	Box<> integerBox3 = new Box<Integer>(); // ???
	Box<Integer> integerBox4 = new Box<>(); // OK c Java SE 7
	Box<Box<Integer>> integerBoxBox = new Box<>(); // OK
}
```

Есть ещё такое понятие, как сырой тип или raw type. Просто дженерик класс или интерфейс без дженерик аргумента)).
```java
	Box box = new Box();
```
Лучше сырыми типами не пользоваться, а то отравитесь ещё.

Бывают случаи, когда нам хочется как-то ограничить тип нашего дженерика. Для этого есть ключевые слова _extends_ и _super_.
```java
/* N может быть любым потомком Number */
public <N extends Number> int doubleNumber(N number) {
    return number.intValue() * 2;
}
/* Для super то же самое, но уже любой предок */
```

Пришло время хайпа. ~~еееЕЕе хайп ууу класс~~. У generic классов не легко понять их подтип. `Box<Integer>` не является наследником `Box<Number>`. Он наследник `Object`'a, как и сам `Box<Number>`. Подробней [тут](https://docs.oracle.com/javase/tutorial/java/generics/inheritance.html).

Теперь мы подошли к моменту, когда стоит рассказать о грустном. Java не знает про дженерики ничего во время [[Архитектура JVM|исполнения кода]]. Это реализовано по историческим причинам в том, числе из-за позиционирования языка _Write Once, Run Anywhere_. Механизм из-за которого это происходит называется стирание типов или type erasure.
За счёт определённой магии компилятор Java сам определяет, где какой тип может быть и подставляет его за место типовых параметров. То есть `contains(T item, T[] array)` превратится в `contains(Object item, Object[] array)`.

По-хорошему, стоит добавить пару слов о `Wildcards`, но вы итак уже устали.

Литература: 
- https://docs.oracle.com/javase/tutorial/java/generics/
- https://neerc.ifmo.ru/wiki/index.php?title=Generics
- https://en.wikipedia.org/wiki/Generics_in_Java
- мозг легенды