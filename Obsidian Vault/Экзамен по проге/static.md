#на3 #на4
Статические члены класса - члены класса, не привязанные к конкретному экземпляру класса. Если позволяет видимость, их можно вызывать, используя имя класса: `ClassName.method()`. Также статические члены и методы можно импортировать командой `import static ClassName.*;`, где вместо \* можно подставить название поля/метода.
Из статических методов можно обращаться только к статическим полям/методам этого класса.
[[nested classes vs inner classes|Про вложенные static и non-static классы]].
Пример:
```java
class Example {
	public static final int a = 1;
	public void foo() {
		System.out.println(a); //OK
	}
	public static void bar() {
		System.out.println(a + 1)); //OK
		foo(); //Error: foo() is not static
	}
}

//main
int b = Example.a; //OK
Example.bar() //OK
```