
# Java Script Lecture_2
## Scope(область видимости)
## Hoisting(подъём)
## Recursion 
## Сlosure(замыкания)

### Что такое Scope (Область Видимости) в JS

Scope в JavaScript определяет область видимости переменных. Когда вы создаете переменную в JavaScript, она доступна только внутри определенной области видимости.

### В JavaScript есть три типа областей видимости:

1. Глобальная область видимости (Global Scope) - **var,let,const**
2. Область видимости функции (Function Scope) - **var**
3. Область видимости блока (Block Scope) - **condition and loop**
4. Module scope:

### Глобальная область видимости (Global Scope) 
- Это область, в которой переменные доступны во всем скрипте. Это означает, что если вы объявляете переменную за пределами всех функций и блоков кода, она будет доступна везде. 

**Например:**

    var x = 10; // глобальная переменная
    function exampleFunction() { 
      console.log(x) ; // доступ к глобальной переменной
    }
    exampleFunction(); // результат: 10

_
### Область видимости функции (Function Scope) 
- Это область, в которой переменные доступны только внутри функции, в которой они были объявлены. Это означает, что переменные, объявленные в функции, не будут доступны за ее пределами.

**Например:**

    function exampleFunction() {
      var x = 10; // переменная, объявленная внутри функции
      console.log(x); // доступ к переменной внутри функции
    }
    exampleFunction(); // результат: 10
    console.log(x); // Ошибка: x не определено

_
### Область видимости блока (Block Scope)
Это область, в которой переменные доступны только внутри блока кода, ограниченного фигурными скобками '{   }'.

**Например:**

    function exampleFunction() {
      if (true) {
        let x = 10; // переменная, объявленная внутри блока if

        console.log(x); // доступ к переменной внутри блока if
      }

     console.log(x); // Ошибка: x не определено
    }

Здесь переменная x доступна только внутри блока if, и не будет доступна за его пределами.


_____
### Hoisting (подъем)
 - это механизм в JavaScript, при котором переменные и функции могут быть объявлены после того, как они были использованы в коде. То есть, JavaScript перемещает объявления переменных и функций вверх в текущую область видимости до выполнения кода.
 
 Hoisting работает для объявлений переменных с использованием ключевых слов **var** и **let**. Для переменных, объявленных с помощью ключевого слова **var**, их объявления перемещаются вверх в текущую область видимости, но значения переменных не изменяются. Для переменных, объявленных с помощью ключевого слова **let**, их объявления также перемещаются вверх в текущую область видимости, но переменные остаются неопределенными до момента их инициализации.

Рассмотрим пример с переменной, объявленной с помощью ключевого слова **var**:


    console.log(x); // undefined
    var x = 10;
    console.log(x); // 10

Когда код выполняется, объявление переменной **x** перемещается вверх в текущую область видимости. В результате, первый **console.log** выводит **undefined**, а второй **console.log** выводит значение **10**.

Рассмотрим пример с переменной, объявленной с помощью ключевого слова **let**:

    console.log(x); // Ошибка: x не определено
    let x = 10;
    console.log(x); // 10

Когда код выполняется, объявление переменной **x** также перемещается вверх в текущую область видимости, но переменная остается неопределенной до момента их инициализации. В результате, первый **console.log** выбрасывает ошибку, а второй **console.log** выводит значение **10**.

**Hoisting** также работает с функциями. Объявления функций перемещаются вверх в текущую область видимости до выполнения кода. Это означает, что вы можете вызвать функцию до ее объявления. 
Например:

    exampleFunction(); // "Привет, мир!"
    function exampleFunction() {
      console.log("Привет, мир!");
    }

Здесь функция **exampleFunction** вызывается до ее объявления, но код работает корректно, так как объявление функции перемещается вверх в текущую область видимости.

Таким образом, понимание механизма hoisting в JavaScript важно для правильного использования переменных и функций в вашем коде. Однако, для избежания путаницы и улучшения читаемости кода, рекомендуется всегда объявлять переменные и функции в начале текущей области видимости, чтобы избежать возможных проблем.

Следует отметить, что hoisting не работает с переменными, объявленными с помощью ключевого слова **const**. Попытка обращения к такой переменной перед ее инициализацией приведет к ошибке.

Кроме того, следует быть осторожными при использовании hoisting, особенно в случае объявления переменных и функций с одинаковыми именами в разных областях видимости. Это может привести к неожиданным результатам, поэтому рекомендуется всегда использовать уникальные имена переменных и функций в вашем коде.

____


### Recursion в JS (Рекурсия)

- **Рекурсия** - это механизм в **JavaScript**, при котором функция вызывает саму себя, чтобы решить задачу. Это мощный инструмент, который может использоваться для решения различных задач, таких как поиск, сортировка, обход дерева и т.д.

Рекурсивная функция состоит из двух частей: базового случая и рекурсивного случая. Базовый случай - это условие, при котором функция не вызывает саму себя, а возвращает результат. Рекурсивный случай - это условие, при котором функция вызывает саму себя для решения подзадачи.

Пример рекурсивной функции для вычисления факториала числа:
      
    function factorial(n) {
      // базовый случай
    if (n === 0) {
    return 1;
      }
      // рекурсивный случай
    else {
    return n * factorial(n-1);
      }
    }
    console.log(factorial(5));** // 120

В этом примере, если **n** равно 0, функция возвращает 1 как базовый случай. Если **n** больше 0, функция вызывает саму себя с аргументом **n-1** для решения подзадачи в рекурсивном случае.

Рекурсия может быть очень мощным и элегантным способом решения задач, но ее использование также может привести к проблемам с производительностью и стеком вызовов. Каждый раз, когда функция вызывает саму себя, это добавляет новый вызов на стек вызовов. Если рекурсивная функция вызывает себя слишком много раз, это может привести к переполнению стека вызовов и возникновению ошибки.

Поэтому, при использовании рекурсии необходимо быть внимательным и проверять, что рекурсивная функция имеет конечный базовый случай и что количество рекурсивных вызовов не превышает допустимых значений.

В целом, рекурсия - это мощный инструмент в **JavaScript**, который может быть использован для решения различных задач. Однако, ее использование должно быть осознанным и ограниченным для избежания потенциальных проблем в вашем коде.
____

 ### Замыкание (closure) в JS
 - **Замыкание (closure)** - это механизм в JavaScript, который позволяет функции запоминать и иметь доступ к переменным из своей внешней области видимости после завершения работы этой области видимости. Это позволяет создавать функции, которые могут сохранять состояние между вызовами и делает их более гибкими и мощными.

 Пример создания замыкания:
 
    function counter() {
    let count = 0;**

    function increment() {
    count++;
    console.log(count);
    }

    return increment;
    }

     const incrementCounter = counter();  
     incrementCounter();** // 1
     incrementCounter();** // 2
     incrementCounter();** // 3

В этом примере функция **counter()** возвращает другую функцию **increment()**, которая имеет доступ к переменной count из внешней области видимости **counter()**. Каждый раз, когда **increment()** вызывается, она увеличивает значение **count** на **1** и выводит его в консоль.

Замыкания также могут использоваться для создания приватных переменных и методов в объектах.

    function createPerson(name) {
      let age = 0;

      return {
        getName() {
          return name;
        },

        getAge() {
          return age;
        },

        incrementAge() {
          age++;
           }
      };
    }

    const person = createPerson("John");

    console.log(person.getName()); // "John"
    console.log(person.getAge()); // 0

    person.incrementAge();

    console.log(person.getAge()); // 1


В этом примере функция **createPerson()** возвращает объект с тремя методами: **getName()**, **getAge()** и **incrementAge()**. Переменная age является приватной и может быть изменена только через метод **incrementAge()**. Методы **getName()** и **getAge()** имеют доступ к переменной **name** и **age** из внешней области видимости **createPerson()**.

**Замыкания** могут быть очень мощным инструментом в JavaScript, но их использование также может привести к утечкам памяти, если не осуществлять правильную управление памятью. Поэтому, при использовании замыканий следует быть внимательным и проверять, что они не создают утечек памяти.

В целом, **замыкания** - это мощный механизм в JavaScript, который позволяет создавать функции с доступом к переменным из своей внешней области видимости. Однако, их использование должно быть осознанным и ограниченным для избежания потенциальных проблем в вашем коде.