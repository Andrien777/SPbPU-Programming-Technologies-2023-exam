#на4
Вложенные классы - классы, объявленные внутри других классов. В отличие от других классов, к ним можно применить любые [[Видимость|модификаторы видимости]].

**Nested классы** - классы, объявленные с модификатором [[static]]. Они не содержат ссылку на класс, в который вложены, и не могут обращаться к нестатическим членам. К nested классам можно обратиться извне, если позволяет видимость.

**Inner классы** - классы, объявленные без модификатора static. Они содержат скрытую ссылку на класс, в который они вложены, и имеют полный доступ к его членам. Доступ извне к inner классам возможен через экземпляр, если позволяет видимость.

Пример:
```java
class Parent {
	private int number = 5;

	public Parent(){}

	public static class Nested {
		public Nested(){}
		public int getNum() {
			return number; //Error, number не видно
		}
	}

	public class Inner {
		public Inner(){}
		public int getNum() {
			return number; //OK
		}
	}
}

//main
Parent p = new Parent();
Parent.Nested n = new Parent.Nested(); //OK

```
