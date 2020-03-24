# `static`

В Java существует специальное ключевое слово `static`, позволяющее указать, что конкретное поле или метод* принадлежит не объекту, а классу.

Примечание*: на самом деле `static` могут быть не только поля и классы, но пока мы будем рассматривать только их.

Что значит "не объекту, а классу"?

Это значит, что для использования этого поля или метода не нужно создавать объект.

С одной стороны это может показать "неправильным", т.к. мы с вами говорили, что весь мир моделируется в виде объектов и взаимодействия между ними.

Но как решили, так решили.

Предназначение `static` в рассматриваемых нами случаях можно описать следующим образом:
* для полей - это чаще всего попытка эмуляции констант, например `PI` или `E`
* для методов - это вспомогательные методы (так называемые хелперы), либо методы, которым не нужен объект для своей работы

Рассмотрим эталонный пример - класс [`Math`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Math.html):
```java
public final class Math {
    /**
     * Don't let anyone instantiate this class.
     */
    private Math() {}

    public static final double E = 2.7182818284590452354;
    public static final double PI = 3.14159265358979323846;
    ...
}
```

Помимо этих двух констант (что такое `final` мы разберём на следующих лекциях), этот класс содержит математические функции:
```java
public final class Math {
    ...
    public static double sin(double a) {
        ...
    }

    public static double cos(double a) {
        ...
    }
    ...
}
```

Использовать `static` поля и методы можно ставя оператор `.` после имени класса, например:
```java
package ru.netology;

public class Main {
  public static void main(String[] args) {
    double result = Math.sin(Math.PI / 2);
    System.out.println(result);
  }
}
```

Это всё здорово, но в тестировании нам такое нужно не часто. Зачем же нам `static`'и?

## Assertions

На самом деле, они нам очень нужны, т.к. все используемые нами assert'ы - это `static` методы класса `Assertions`:

```java
public class Assertions {
    ...
    public static void assertTrue(boolean condition) {
        ...
    }
    ...
	public static void assertFalse(boolean condition) {
        ...
	}
}
```

Это позволяет нам не создавать объект из этого класса (тем более конструктор у него `protected`), а просто использовать нужные нам методы:
```java
package ru.netology;

import org.junit.jupiter.api.Assertions;
import org.junit.jupiter.api.Test;

class SampleTest {
  @Test
  public void shouldPass() {
    Assertions.assertTrue(true);
  }
}
```

Но раньше же мы не писали `Assertions`, а просто писали `assertTrue`?

## `static` import

В Java есть специальный механизм, который позволяет нам использовать статические поля и методы без указания класса.

Для этого используется специальный static import:
```java
package ru.netology;

import org.junit.jupiter.api.Test;

import static org.junit.jupiter.api.Assertions.assertTrue; // <- static import

class SampleTest {
  @Test
  public void shouldPass() {
    assertTrue(true); // <- теперь можно не писать Assertions.
  }
}
```

Когда вы используете много методов (а не один), то обычно static import превращается в import со * (что означает все статические поля и методы):
```java
package ru.netology;

import org.junit.jupiter.api.Test;

import static org.junit.jupiter.api.Assertions.*; // <- static import

class SampleTest {
  @Test
  public void shouldPass() {
    assertTrue(true); // <- теперь можно не писать Assertions.
  }
}
```

static import повсеместно используется в тестировании (не только в JUnit), поэтому привыкайте к этому. Если вы видите где-то вызов метода, но перед методом ничего нет, то с большой вероятностью, это статический метод, импортированный с помощью static import.

## Утилитные классы

Есть общепринятое соглашение (которому, к сожалению, следуют не все), что классы, которые содержат **только** статические методы, называть утилитными и использовать специальный формат оформления:
1. Класс пишется во множественном числе и оканчивается на `s`, например `Assertions`, `Collections`, `Arrays`
1. Класс не имеет публичного конструктора (во избежание создания объектов этого класса)

Мы рекомендуем вам придерживаться этого соглашения (если вы собираетесь разрабатывать подобные классы).
