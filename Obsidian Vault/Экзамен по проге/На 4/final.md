#на4
final - ключевое слово, модификатор, регулирующее наследование.
Применительно к классам final запрещает наследование.
Применительно к полям, final запрещает переопределение в наследниках и присваивание после первого присваивания в конструкторе или при инициализации.
Применительно к методам, final запрещает переопределение в наследниках.
```java
final class Example {

	public final int a = 1;
	private final int b;
	
	Example() {
		b = 1;
	}
	
	public void foo() {
		b++; //Error, can't reassign final b
	}
}

class ExampleSubclass extends Example {} //Error, can't inherit final class

//main
Example e = new Example;
e.a = 2; //Error, can't reassign final a
```