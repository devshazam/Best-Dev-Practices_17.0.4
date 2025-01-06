## Java — продвинутый уровень

#### Содержание
* Многопоточность и асинхронность
* Структуры данных
* Garbage Collection

🏆 Правильных ответов: 10 из 13.

#### Q1. Что выведет программа?

```java
public class Main {
    public static void foo(Integer i) {
        System.out.println("foo(Integer)");
    }
    public static void foo(short i) {
        System.out.println("foo(short)");
    }
    public static void foo(long i) {
        System.out.println("foo(long)");
    }
    public static void foo(Object i) {
        System.out.println("foo(object)");
    }
    public static void foo(int... i) {
        System.out.println("foo(int...)");
    }
    public static void main (String[] args) {
    foo (10);
    }
}
```

- [x] foo(long)

#### Q2. Что будет выведено при исполнении данного участка кода?

```java
class SomeClass {
    public static int field = 0;
}

public class Main {
    public static void main(String[] args) {
        SomeClass someClass1 = new SomeClass();
        someClass1.field++;
        SomeClass someClass2 = new SomeClass();
        someClass2.field++;
        SomeClass someClass3 = new SomeClass();
        someClass3.field++;

        SomeClass.field++;
        ++SomeClass.field;
        System.out.println(++SomeClass.field);
    }
}
```

- [x] 6

#### Q3. Что будет выведено при исполнении данного кода?

```java
public class Main {
    static boolean foo(char a) {
        System.out.print(a);
        return true;
    }
    public static void main(String[] args) {
        int i = 0;
        for (foo('A'); foo('B') && (i<2); foo('C')){
            i++;
            foo('D');
        }
    }
}
```

- [x] ABDCBDCB

#### Q4. Каким будет результат выполнения данного кода?

```java
Integer a = 100;
Integer b = 100;
Integer c = 200;
Integer d = 200;
Integer e = Integer.valueOf(100);
Integer f = Integer.valueOf(200);
System.out.println(a==b);
System.out.println(c==d);
System.out.println(e==a);
System.out.println(f==c);
```

- [x] true false true false

#### Q5. Какой из перечисленных типов НЕ является reifiable?

- [x] List<?>[]

#### Q6. Каким способом в Java достигается полиморфизм?

- [x] Переопределение методов

#### Q7. Каков результат работы этого кода?

```java
public class SomeClass {
    static int i = 1;
}

public class ExceptionTest {
    public static void main(String[] args) {
        System.out.println(foo());
    }

    static int foo() {
        try {
            SomeClass someClass = null;
            return someClass.i;
        } catch (Exception e) {
            return 2;
        } catch (Throwable e) {
            return 3;
        } finally {
            return 4;
        }
    }
}
```

- [x] 4

#### Q8. У вас есть 10 потоков, которые одновременно обращаются к одному и тому же ресурсу - очереди задач, реализованной с помощью `BlockingQueue`. Вам необходимо реализовать механизм, который гарантирует, что не более 5 потоков одновременно могут обрабатывать задачи из очереди. Какой из следующих способов НЕ подходит для решения этой задачи?

- [ ] Использовать `CountDownLatch` с начальным значением 5 и каждый раз перед получением задачи из очереди вызывать метод `await()` у `CountDownLatch`. Когда поток заканчивает обработку задачи, он вызывает `countDown()`
- [ ] Использовать `ExecutorService` с фиксированным размером пула потоков, равным 5, и запускать все потоки через этот пул
- [ ] Использовать `ReentrantLock` для блокировки доступа к очереди задач, а внутри блокировки проверять, не превышает ли количество обрабатывающих задач 5, и, если да, ждать освобождения блокировки
- [ ] Создать отдельный класс-посредник, который будет обрабатывать запросы на получение задач из очереди и запускать обработку задач только для 5 потоков одновременно
- [ ] Использовать `Semaphore` с начальным значением 5 и каждый раз перед получением задачи из очереди вызывать метод `acquire()` у семафора, а после обработки задачи — `release()`

#### Q9. Какая структура данных из перечисленных НЕ является lock-free?

- [x] Atomiclnteger

#### Q10. Что из перечисленных функциональных ограничений синхронизации в Java является ЛОЖЬЮ?

- [x] Volatile переменная гарантирует атомарность последовательности читать-модифицировать-читать

#### Q11. В компании N наняли junior разработчика. Первой его задачей было написать несложный асинхронный код, который последовательно вызывает сервисы с некоторыми условиями. После вызова сервиса должен одновременно вызываться сервис 2 и сервис 3. Если на момент вызова сервиса 3 вызов сервиса 2 еще на завершен - задача на вызов сервиса 3 ожидает ответа от сервиса 2 и печатает лог об ожидании. Junior разработчик написал следующий код и попросил сделать Вас ревью. Допустили бы Вы данный код в продакшн? (Обработкой ошибок можно пренебречь).

```java
final var service2Called = new AtomicBoolean(false);
final var first = CompletableFuture.supplyAsync(() -> {
    callService();
    return "result";
});
final var second = first.thenAcceptAsync(_ -> {
    callService();
    service2Called.compareAndSet(false, true);
});
final var third = first
        .thenRun(() -> {
            if (service2Called.compareAndSet(false, true)) {
                second.join();
            }
        })
        .thenAccept(_ -> {
            callService();
        });
```

- [ ] Нет. Лучше использовать метод thenCombine на вызове третьего сервиса и передать в него вызов второго сервиса первым параметром
- [ ] Да. С кодом все хорошо
- [ ] Код невалиден, вместо использования CompletableFuture chain Паша должен просто сделать Future для вызова первого сервиса и сделать на нем join. Затем линейно вызвать сначала сервис 2, а затем сервис 3
- [ ] Нет. Вместо thenAccept и thenRun (в случае сервиса 3) надо использовать thenAcceptAsync и thenRunAsync
- [ ] Данный код валиден, но для третьего и второго сервиса необязательно передавать результат вызова первого сервиса. thenAccept можно заменить на thenRun

#### Q12. Какие структуры данных требуют, чтобы данные реализовывали интерфейс Comparable?

- [x] TreeMap

#### Q13. После продолжительной работы сервиса графики показали, что память постепенно растет. Вы попросили вашего напарника проинспектировать код на наличие утечки памяти. Через пару дней он пришел с результатом, что утечкой памяти является цикличная ссылка в коде класса реализации графа. Выглядит это следующим образом. Может ли это быть причиной утечки памяти? (в качестве GC используется ParallelGC).

```java
class Node {
    private Node edge = null;
    public Node getEdge() {
        return edge;
    }
    public void setEdge(Node edge) {
        this.edge = edge;
    }
}
public void createAndDelete() {
    final var node1 = new Node();
    final var node2 = new Node();

    node1.setEdge(node2);
    node2.setEdge(node1);
}
```

- [ ] Да. ParalleIGC не умеет работать с циклическими ссылками, поэтому каждый вызов метода createAndDelete() увеличивает количество неуничтожаемых объектов.
- [ ] Нет. Данные объекты не аллоцируются на куче при такой логике и тем самым не вызывают утечку.
- [ ] Да. Так как у объектов с циклическими ссылками надо вызывать метод finalize() чтобы он очистился. Иначе GC не может их удалить.
- [ ] Да. Из за цикличности ссылок объекты не могут быть перемещены из молодого поколения в старое
