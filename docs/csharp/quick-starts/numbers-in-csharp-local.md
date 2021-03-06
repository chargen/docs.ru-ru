---
title: Руководство по числам в C#. Краткие руководства по локальной разработке на C#
description: Изучите C# на примере числовых типов, их свойств и методов.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: cf8f00193b4fa66ff444fe8e40942c39e99d10b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="numbers-in-c-quickstart"></a>Краткое руководство по числам в C#

Это краткое руководство поможет в интерактивном изучении числовых типов в C#. Вы напишете небольшие фрагменты кода, затем скомпилируете и выполните этот код. Это краткое руководство содержит ряд уроков, в которых рассматриваются числа и математические операции в C#. В рамках этих занятий вы ознакомитесь с основами языка C#.

Для работы с этим кратким руководством вам потребуется компьютер, который можно использовать для разработки. В руководстве по [началу работы с .NET за 10 минут](https://www.microsoft.com/net/core) содержатся инструкции по настройке локальной среды разработки на компьютерах Mac, Windows или Linux. Краткий обзор команд, которые будут здесь использоваться, и ссылки на дополнительные сведения представлены в [вводной статье к руководствам по локальной разработке](local-environment.md).

## <a name="explore-integer-math"></a>Вычисления с целыми числами

Создайте каталог с именем **numbers-quickstart**. Откройте этот каталог и выполните команду `dotnet new console -n NumbersInCSharp -o .`.

Откройте файл **Program.cs** в любом редакторе и замените строку `Console.Writeline("Hello World!");` следующим кодом:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Чтобы выполнить этот код, введите `dotnet run` в окно командной строки. 

Вы увидели одну из основных математических операций с целыми числами. Тип `int` представляет **целое** положительное или отрицательное число. Для сложения используйте символ `+`. Другие стандартные математические операции с целыми числами включают:

- `-` — вычитание;
- `*` — умножение;
- `/` — деление.

Начните с ознакомления с различными операциями. Добавьте следующие строки после строки, с помощью которой записывается значение `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Чтобы выполнить этот код, введите `dotnet run` в окно командной строки. 
    
Можно также поэкспериментировать, выполнив несколько математических операций в одной строке. Например, выполните `c = a + b - 12 * 17;`. Допускается сочетание переменных и постоянных чисел.

> [!TIP]
> Вероятнее всего, при изучении C# (как и любого другого языка программирования) вы будете допускать ошибки в коде. **Компилятор** найдет эти ошибки и сообщит вам о них. Если результат содержит сообщения об ошибках, внимательно просмотрите пример кода и код в окне, чтобы понять, что нужно исправить.
> Это упражнение поможет вам изучить структуру кода C#.     

Вы завершили первый этап. Прежде чем перейти к следующему разделу, переместим текущий код в отдельный метод. Это упростит начало работы с новым примером. Переименуйте метод `Main` в `WorkingWithIntegers` и запишите новый метод `Main`, который вызывает `WorkingWithIntegers`. В результате ваш код должен выглядеть примерно следующим образом:

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a>Изучение порядка операций

Закомментируйте вызов `WorkingWithIntegers()`. Это поможет упорядочить выходные данные в этом разделе.

```csharp
//WorkingWithIntegers();
```

`//` запускает **комментарий** в C#. Комментарии — это любой текст, который должен быть сохранен в исходном коде, но не должен выполняться как код. Компилятор не создает исполняемый код из комментариев.

Язык C# определяет приоритет математических операций в соответствии с правилами математики.
Умножение и деление имеют приоритет над сложением и вычитанием.
Убедитесь в этом, добавив следующий код в метод `Main` и выполнив команду `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

В выходных данных видно, что умножение выполняется раньше сложения.

Можно применить другую последовательность операций. Для этого операции, которые должны выполняться первыми, нужно заключить в скобки. Добавьте приведенные ниже строки и выполните код еще раз.

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

Поэкспериментируйте, объединяя различные операции. Добавьте в конец метода `Main` строки, подобные приведенным ниже. Выполните `dotnet run` еще раз.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Возможно, вы заметили интересное поведение целых чисел. Деление целых чисел всегда дает результат в виде целого числа, даже если ожидаемый результат содержит десятичную или дробную часть.

Если вы еще не видели пример такого поведения, добавьте следующий код в конец метода `Main`:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

Выполните `dotnet run` еще раз, чтобы просмотреть результаты.

Прежде чем продолжить, давайте поместив весь код, который вы написали в этом разделе, в новый метод. Вызовите этот новый метод `OrderPrecedence`.
Результат должен выглядеть примерно так:

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {   
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a  + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a>Изучение точности и ограничений для целых чисел
В последнем примере вы увидели, что при делении целых чисел результат усекается.
Вы можете получить **остаток** с помощью оператора **остатка от деления**, который обозначается символом `%`. Попробуйте добавить приведенный ниже код в метод `Main`.

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Тип целых чисел C# характеризуется еще одним отличием от математических целых: тип `int` имеет минимальные и максимальные ограничения. Добавьте следующий код в метод `Main`, чтобы просмотреть эти ограничения:
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Если при вычислении выводится значение вне этих пределов, возникает условие **потери значимости** или **переполнения**. Ответ должен находиться в диапазоне от минимального до максимального значения. Добавьте следующие две строки в метод `Main`, чтобы увидеть пример:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
Обратите внимание, что ответ очень близок к минимальному целому числу (отрицательное значение). Он совпадает со значением `min + 2`. Оператор сложения **вызвал переполнение** допустимых значений для целых чисел.
Ответ является очень большим отрицательным числом, так как переполнение покрывает диапазон от наибольшего целого числа до наименьшего.

Существуют другие числовые типы с различными ограничениями и точностью, которые можно использовать, если тип `int` не соответствует вашим требованиям. Рассмотрим их.

Давайте еще раз переместим код, написанный в этом разделе, в отдельный метод. Присвойте обработчику события имя `TestLimits`. 

## <a name="work-with-the-double-type"></a>Работа с типом double

Числовой тип `double` представляет число с плавающей запятой двойной точности. Эти термины могут быть новыми для вас. Число **с плавающей запятой** можно использовать для представления нецелых чисел, которые могут быть очень большими или малыми. **Двойная точность** означает, что для хранения этих чисел используется большая точность, чем **одиночная**. На современных компьютерах числа с двойной точностью используется чаще, чем с одиночной.
Рассмотрим их. Добавьте следующий код и просмотрите результат:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Обратите внимание, что ответ включает десятичную долю частного. Попробуйте более сложное выражение с типом double:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

Диапазон значений типа double гораздо больше, чем диапазон значений целых чисел. Добавьте следующий фрагмент после написанного кода:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Значения выводятся в экспоненциальном представлении. Число слева от символа `E` является значащим. Число справа — это показатель степени, который равен 10. 

Так же, как десятичные числа в математике, значения double в C# могут содержать ошибки округления. Выполните этот код:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Вы знаете, что периодическая десятичная дробь `0.3` не равняется `1/3`.

***Задача***

Выполните другие вычисления с большими числами, малыми числами, умножением и делением с помощью типа `double`.  Попробуйте выполнить более сложные вычисления.

После того как вы решите сложную задачу, поместите написанный код в новый метод. Присвойте этому методу имя `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Работа с типами с фиксированной запятой

Вы уже ознакомились с базовыми числовыми типами в C# — целыми числами и числами типа double.  Осталось изучить еще один тип: `decimal`. Тип `decimal` имеет меньший диапазон, но большую точность, чем `double`. Термин **фиксированная запятая** означает, что десятичный (или двоичный) разделитель не перемещается. Например:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Обратите внимание, что диапазон меньше, чем для типа `double`. Вы можете убедиться в повышении точности при использовании типа decimal, выполнив следующий код:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

Суффикс `M` возле чисел указывает, что для константы должен использоваться тип `decimal`.

Обратите внимание, что при вычислении с использованием типа decimal справа от запятой содержится больше цифр. 

***Задача***

Теперь, когда вы ознакомились с разными числовыми типами, напишите код, который позволяет вычислить площадь круга с радиусом 2,50 см. Помните, что площадь круга равна квадрату радиуса, умноженному на число пи. Подсказка: в .NET есть константа пи <xref:System.Math.PI?displayProperty=nameWithType>, которую можно использовать. 

Вы должны получить ответ от 19 до 20.
Ответ можно [просмотреть в готовом примере кода в GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).

При желании поэкспериментируйте с другими формулами. 

Вы выполнили все задачи краткого руководства по числам в C#. Теперь вы можете выполнить руководство по [ветвям и циклам](branches-and-loops-local.md) в своей среде разработки.

Дополнительные сведения о числах в C# см. в следующих статьях:

[Таблица целых типов](../language-reference/keywords/integral-types-table.md)   
[Таблица типов с плавающей запятой](../language-reference/keywords/floating-point-types-table.md)   
[Таблица встроенных типов](../language-reference/keywords/built-in-types-table.md)   
[Таблица неявных числовых преобразований](../language-reference/keywords/implicit-numeric-conversions-table.md)   
[Таблица явных числовых преобразований](../language-reference/keywords/explicit-numeric-conversions-table.md)

