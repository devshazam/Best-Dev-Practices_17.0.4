## Python — продвинутый уровень

🏆 Правильных ответов: 28 из 32. Вопросы в тесте по Python могут отличаться от приведенных. Здесь собрана некая база из возможных вопросов, пользуйтесь поиском

#### Q1. Вы используете список для хранения информации о посещенных веб-страницах. Какая особенность списка может привести к проблемам при таком использовании?

- [x] При добавлении новых элементов в список могут возникать дубликаты

#### Q2. Какова сложность алгоритма, представленного следующим фрагментом кода?

```
total = 0
for i in range(n):
    for j in range(n):
        total += 1
```

- [x] O(n^2)

#### Q3. Какой результат выведет этот код?

```
def add(a=[]):
    a.append('A')
    return a

print(add())
print(add())
```

- [x] ['A'] и ['A', 'A']

#### Q4. Вы работаете с большим набором данных и вам необходимо определить, какая из перечисленных встроенных функций Python наиболее эффективна для определения длины списка с использованием меньшего объема оперативной памяти.

- [x] len()

#### Q5. Что будет результатом выполнения кода?

```
class Vehicle:
    def __init__(self, speed=0):
        self.speed = speed

    def accelerate(self, increment):
        self.speed += increment / 2

class Car(Vehicle):
    def __init__(self, speed=0, fuel=100):
        super().__init__(speed)
        self.fuel = fuel

    def accelerate(self, increment):
        super().accelerate(increment * 2)
        self.fuel -= increment / 2

my_sedan = Car(fuel=50)
my_pickup = Vehicle()
my_sedan.accelerate(10)
my_pickup.accelerate(20)

print("Седан, едущий со скоростью {} км/ч с топливом {:.0f}%".format(my_sedan.speed, my_sedan.fuel))
print("Пикап, едущий со скоростью {} км/ч".format(my_pickup.speed))
```

- [x] Седан, едущий со скоростью 10.0 км/ч с топливом 45% и Пикап, едущий со скоростью 10.0 км/ч

#### Q6. Что вернет этот код?

```
word = "PyThoN ExAmP1E"
result = [(i, char) for i, char in enumerate(word) if char.islower()]
print(result)
```

- [x] [(1, 'y'), (3, 'h'), (4, 'o'), (9, 'm')]

#### Q7. Какое из следующих утверждений верно?

- [x] Модуль collections предлагает такие типы данных, как namedtuple и Counter

#### Q8. Что следует предпринять при работе с файлами в Python для избежания потери данных или повреждения файла?

- [x] Использовать блок with для автоматического закрытия файла после выхода из блока

#### Q9. Выберите ответ, в котором указаны только те варианты, для которых следующее выражение вернет значение True.

```
re.match(r"^(info|sales|support)@\w+\.(com|net|org)$", text) is not None
```

- [x] A, B, C

#### Q10. Что из перечисленного НЕ является преимуществом использования lambda функций вместе с map и filter в Python?

- [x] Возможность возвращения нескольких значений из одной lambda-функции

#### Q11. Какой из следующих вариантов является верным использованием конструкции finally в обработке исключений в Python?

- [x] Выполнение кода, необходимого для освобождения ресурсов независимо от того, произошло исключение или нет

#### Q12. Какой функции из модуля itertools соответствует по смыслу код ниже?

```
def compress_data(data, selectors):
    return (d for d, s in zip(data, selectors) if s)
```

- [x] compress

#### Q13. Какой из вариантов является НЕПРАВИЛЬНЫМ использованием декоратора, когда функция требует аргументов?

- [x] 
```
def decorator(func):
    return func(10, 5)
```

#### Q14. Что выводит следующий код?

```
def countdown(num):
    while num > 0:
        yield num
        num -= 1

generator = countdown(2)
print(next(generator))
print(next(generator))
```

- [x] 2, 1

#### Q15. Какой метод обработки данных в Python наилучшим образом демонстрирует использование модели "ленивых вычислений"?

- [x] Использование generator expression для поэлементной обработки данных

#### Q16. Какой из следующих методов в Python используется для обеспечения безопасного доступа к общим ресурсам из нескольких потоков, предотвращая состояние гонки?

- [x] threading.Lock

#### Q17. Укажите, каким будет вывод этой программы в случае, если на вход подаются две строки — сначала «Python», потом «exit».

```
name = ''
while True:
   c = input()
   if c == 'exit':
      break
   name = name + c
print('I’m', name)
```

- [x] I’m Python

#### Q18. Следующий код выводит ошибку. Почему?

```
tuple_ex = ('a', 'b', 'c', {'d': 4})
tuple_ex.append('e', 'f')
new_elements = ('g', 'h')
new_tuple = tuple_ex + new_elements


print(len(tuple_ex))
print(len(new_tuple))
```

- [x] Метод append ожидает только один аргумент

#### Q19. Какой результат выведет этот код?

```
def add(a=[]):
   a.append('A')
   return a

print(add())
print(add())
```

- [x] ['A'] и ['A', 'A']

#### Q20. Какая процедура или функция заранее НЕ определена в модуле os?

- [x] Создание нового потока

#### Q21. Какой результат выведет этот код?

```
class A:
   counter = 0
   def meth(self):
      return 'method'
a = A()
a.counter = 100

print('Equals' if a.counter == A.counter else 'Not Equals')
print('Equals' if a.meth() == A.meth(a) else 'Not Equals')
```

- [x] Not Equals и Equals

#### Q22. Какой из утверждений НЕВЕРНО?

- [x] Как seek(), так и truncate() применимы к файлам, открытым в режиме добавления (‘a’)

#### Q23. Следующий код выводит результат: ['0: a = x', '1: b = y', '2: c = z']. Что пропущено в print()?

```
keys = ['a', 'b', 'c']
values = ['x', 'y', 'z']
idxs = enumerate(zip(keys, values))
print(...)
```

- [x] `list(f'{i}: {k} = {v}' for i, (k, v) in idxs)`

#### Q24. Выберите НЕВЕРНОЕ утверждение.

- [x] Reduce возвращает массив элементов, а map — одно значение

#### Q25. Выберите верное утверждение о блоке try-except-finally в Python.

- [x] Код в блоке finally будет выполнен независимо от того, возникло исключение в блоке try или нет

#### Q26. Какой из встроенных типов данных Python лучше всего подходит для реализации стека?

- [x] Списки

#### Q27. Выберите операцию, которую НЕЛЬЗЯ выполнить с помощью библиотеки requests.

- [x] Использовать асинхронные HTTP-запросы

#### Q28. Какой функции из модуля itertools соответствует по смыслу код ниже?

```
def func(*iterables):
   for it in iterables:
      for e in it:
         yield e
```

- [x] chain

#### Q29. Укажите, какое число тестов будет завершено c успехом при использовании библиотеки pytest для кода, представленного ниже:

```
import pytest, unittest

def should_skip():
   return True

class Test(unittest.TestCase):
   def a(self):
      self.assertEqual(1 + 1, 2)
   def test_b(self):
      self.assertEqual(1 + 2, 3)

   @pytest.mark.skip
   def test_c(self):
      self.assertEqual(1 + 3, 4)

   @pytest.mark.skipif('should_skip')
   def test_d(self):
      self.assertEqual(1 + 4, 5)
```

- [x] 1

#### Q30. Выберите ответ, в котором указаны только те варианты, для которых следующее выражение вернет значение True.

```
re.match(r"^\+7-(\d{3,5})-\d{3,5}?", text) is not None

A. +7-(123)-45678
B. +7-123-45678
C. +7-12-345678
D. +7-(1234)-5678
E. +7-12345-678
```

- [x] B, E

#### Q31. В каком из вариантов генератор реализован НЕВЕРНО?

- [x] `list(i*i for i in range(5))[3]`

#### Q32. Какое утверждение о декораторе lru_cache НЕВЕРНО?

- [x] По умолчанию lru_cache предназначен для кэширования результатов функции в пределах одного процесса Python
