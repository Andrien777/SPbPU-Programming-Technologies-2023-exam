#на4
### Queue
Queue - интерфейс коллекции, реализующей [[Стеки, очереди#Очередь|очередь]].

Методы:
* add(E)/offer(E) - добавить
* remove()/poll() - удалить и вернуть удаленный
* element()/peek() - вернуть элемент из начала, не удаляя

Реализации:
* Скелетальная:
	* AbstractQueue
* Полная:
	* [[ArrayList, LinkedList#LinkedList|LinkedList]]

### Deque
#на5
Deque - интерфейс коллекции, реализующей двустороннюю очередь, т.е. добавлять и удалять элементы можно с обоих концов.

Методы:
* addFirst(E)/offerFirst(E)
* addLast(E)/offerLast(E)
* removeFirst()/pollFirst()
* removeLast()/pollLast()
* getFirst()/peekFirst()
* getLast()/peekLast()
* push()
* pop()
push() и pop() обеспечивают работу с Deque как со [[Стеки, очереди#Стек|стеком]].

Реализации:
* ArrayDeque - на основе массива. Примерно можно представить как достаточно большой закольцованный массив с индексами головы и хвоста очереди
* [[ArrayList, LinkedList#LinkedList|LinkedList]]