#на3 
Object.toString() - метод для приведения объекта к строковому представлению. Используется для вывода на консоль и не только, а также дебаггер IDEA использует именно toString() для отображения значения переменных. Как и [[equals|equals()]], toString() определен в Object и составляет представление в формате ИмяКласса@[[hashCode]]. Пример написания:
```java
class Point {
	private String name;
	private int x;
	private int y;
	//Конструктор, get, set...
	@Override
	public String toString() {
	    return String.format(LOCALE_ENGLISH, "%s(%d; %d)", name, x, y);
	}
}
```