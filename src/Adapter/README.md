# Адаптер

### Назначение
Адаптер предназначен для преобразования интерфейса класса к другому интерфейсу, на который рассчитан клиент.


### Пример

Мы переписываем старый проект и используем итераторы, которые имплементируют интерфейс [Iterator](Iterator.java).
Но в нашем проекте есть всё ещё куча легаси, которое использует интерфейс [Enumeration](Enumeration.java).
Как нам работать с легаси кодом, если мы хотим использовать интерфейс [Iterator](Iterator.java).

### Решение
Нам необходимо создать класс [адаптер](EnumerationIterator.java), который преобразует классы старого интерфейса в новый.

Адаптер наследует новый интерфейс [Iterator](Iterator.java). В него прокидываем старый легаси интерфейс [Enumeration](Enumeration.java)
и вызываем его методы.

Но Iterator содержит новый метод `remove`, которого нет в старом интерфейсе.
В нашем примере мы просто бросаем исключение `UnsupportedOperation`.
Оно немного ломает логику поведения интерфейса [Iterator](Iterator.java),
поэтому этот адаптер нужно хорошо документировать и осторожно использовать.
 
> Паттерны `Адаптер` и `Декоратор` довольно похожи по коду, но по назначению они кардинально отличаются.
> Адаптер преобразует классы одного интерфейса в другой.
> А декоратор просто расширяет класс без его изменения.