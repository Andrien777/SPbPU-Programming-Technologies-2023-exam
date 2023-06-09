#на3 
Object.equals() - метод для сравнение объектов на равенство по значению, в отличие от оператора \==, сравнивающего ссылочные типы по ссылке. То, что объекты ссылочного типа равны по ссылке означает, что они ссылаются на одни и те же объекты в памяти и, соответственно, при изменении этих объектов в памяти с помощью одной ссылки изменятся объекты по всем ссылкам. Равенство по значению означает, что в объектах хранятся одинаковые данные, но, возможно, в разных местах в памяти. Равные по ссылке объекты автоматически равны по значению. Стандартный пример написания equals():
```java
class Point {
    private int x;
    private int y;
    //Конструктор, get, set...
    @Override
    public boolean equals(Object other) {
        if(this == other) return true;
        if(other instanceof Point p) {
            return (this.x == p.getX()) && (this.y == p.getY());
        }
        return false;
    }
}
```
equals() объявляется с аннотацией @Override, так как эта функция определена в Object, от которого наследуются все классы, как сравнение по ссылке.

equals() должен удовлетворять определенным [[hashCode#Свойства equals|свойствам]].