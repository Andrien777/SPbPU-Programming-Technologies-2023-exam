#на3 #на4
enum - класс с конечным числом экземпляров, каждый из которых  определен изначально. 
Пример:
```java
enum DayOfWeek { 
	MONDAY, 
	TUESDAY, 
	WEDNESDAY, 
	THURSDAY, 
	FRIDAY, 
	SATURDAY,
	SUNDAY
}
```
enum всегда наследуется от **Enum**.
Экземпляры доступны как public static, допустимо сравнение \==.
Методы, унаследованные от Enum для экземпляров:
* name() - имя экземпляра
* toString() определен так же, как и name()
* ordinal() - порядковый номер экземпляра в enum, начиная с 0
static методы класса:
* valueOf(String) - экземпляр с таким названием
* values() - массив всех экземпляров
[[Generics|Дженерики]] в enum использовать нельзя.
enums - полноценные классы. В них можно объявлять поля и методы. При этом задание экземпляров подразумевает вызов конструктора, в который можно передавать параметры. Пример:
```java
enum DayOfWeek { 
	MONDAY(false), 
	TUESDAY(false), 
	WEDNESDAY(false), 
	THURSDAY(false), 
	FRIDAY(false), 
	SATURDAY(true),
	SUNDAY(true);

	private boolean isWeekend;
	
	public DayOfWeek(boolean isWeekend) {
		this.isWeekend = isWeekend;
	}

	public boolean isWeekend() {
		return this.isWeekend();
	}
}

//main
DayOfWeek day = DayOfWeek.MONDAY;
System.out.println(day.name() + (day.isWeekend()) ? " is " : " isn't " + "weekend.") //MONDAY isn't weekend.
```

Enum может быть [[abstract class vs interface|абстрактным классом]], каждый экземпляр которого переопределяет абстрактные методы. Т.е. каждый элемент - унаследованный от enum [[Локальные классы, Анонимные классы#Анонимные классы|анонимный класс]].
![[Pasted image 20230601213953.png]]