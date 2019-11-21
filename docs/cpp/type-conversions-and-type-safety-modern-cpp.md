---
title: Type conversions and type safety
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
ms.openlocfilehash: dbca9057622ab1a92b74e2958b8dfbe8d810fede
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246112"
---
# <a name="type-conversions-and-type-safety"></a>Type conversions and type safety

En este documento se identifican problemas comunes de la conversión de tipos y se describe cómo evitarlos en el código de C++.

Cuando se escribe un programa de C++, es importante asegurarse de tiene seguridad de tipos. Esto significa que cada variable, argumento de función y valor devuelto de una función almacena una clase aceptable de datos y que las operaciones que implican valores de distintos tipos “tienen sentido” y no provocan pérdida de datos, interpretaciones incorrectas de los patrones de bits o daños en la memoria. Un programa que nunca convierte valores de un tipo a otro de forma implícita o explícita tiene seguridad de tipos por definición. No obstante, las conversiones de tipos se requieren a veces, incluso las no seguras. For example, you might have to store the result of a floating point operation in a variable of type **int**, or you might have to pass the value in an unsigned **int** to a function that takes a signed **int**. Both examples illustrate unsafe conversions because they may cause data loss or re-interpretation of a value.

Cuando el compilador detecta una conversión no segura, emite un error o una advertencia. Un error detiene la compilación; una advertencia permite que la compilación continúe, pero indica un posible error en el código. Sin embargo, aunque el programa se compile sin advertencias, todavía pueden contener código que lleve a conversiones implícitas que generan resultados incorrectos. Pueden producirse errores de tipos en el código debido a las conversiones explícitas.

## <a name="implicit-type-conversions"></a>Conversiones de tipos implícitas

When an expression contains operands of different built-in types, and no explicit casts are present, the compiler uses built-in *standard conversions* to convert one of the operands so that the types match. El compilador intenta las conversiones en una secuencia bien definida hasta que una sea correcta. Si la conversión seleccionada es una promoción, el compilador no emite una advertencia. Si la conversión es una restricción, el compilador emite una advertencia sobre la posible pérdida de datos. El hecho de que se produzca en efecto la pérdida de datos depende de los valores reales implicados, pero se recomienda tratar esta advertencia como un error. Si está implicado un tipo definido por el usuario, el compilador intenta utilizar las conversiones especificadas en la definición de clase. Si no encuentra una conversión aceptable, el compilador emite un error y no se compila el programa. For more information about the rules that govern the standard conversions, see [Standard Conversions](../cpp/standard-conversions.md). For more information about user-defined conversions, see [User-Defined Conversions (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md).

### <a name="widening-conversions-promotion"></a>Conversiones de ampliación (promoción)

En una conversión de ampliación, un valor de una variable menor se asigna a una variable mayor sin pérdida de datos. Dado que las conversiones de ampliación siempre son seguras, el compilador las realiza de forma silenciosa y no emite advertencias. Las conversiones siguientes son de ampliación.

|De|En|
|----------|--------|
|Any signed or unsigned integral type except **long long** or **__int64**|**double**|
|**bool** or **char**|Cualquier otro tipo integrado|
|**short** or **wchar_t**|**int**, **long**, **long long**|
|**int**, **long**|**long long**|
|**float**|**double**|

### <a name="narrowing-conversions-coercion"></a>Conversiones de restricción (coerción)

El compilador realiza las conversiones de restricción implícitamente, pero le advierte sobre la pérdida de datos. Tome estas advertencias muy en serio. Si está seguro de que no se producirá ninguna pérdida de datos porque los valores de la variable mayor cabrán siempre en la variable menor, agregue una conversión explícita de modo que el compilador no emita ninguna advertencia más. Si no está seguro de que la conversión es segura, agregue alguna clase de código de comprobación en tiempo de ejecución para controlar la posible pérdida de datos a fin de que no cause resultados incorrectos en el programa.

Cualquier conversión de un tipo de punto flotante a un tipo entero es una conversión de restricción porque la parte fraccionaria del valor de punto flotante se descarta y se pierde.

El ejemplo de código siguiente muestra algunas conversiones de restricción implícitas y las advertencias correspondientes que emite el compilador.

```cpp
int i = INT_MAX + 1; //warning C4307:'+':integral constant overflow
wchar_t wch = 'A'; //OK
char c = wch; // warning C4244:'initializing':conversion from 'wchar_t'
              // to 'char', possible loss of data
unsigned char c2 = 0xfffe; //warning C4305:'initializing':truncation from
                           // 'int' to 'unsigned char'
int j = 1.9f; // warning C4244:'initializing':conversion from 'float' to
              // 'int', possible loss of data
int k = 7.7; // warning C4244:'initializing':conversion from 'double' to
             // 'int', possible loss of data
```

### <a name="signed---unsigned-conversions"></a>Conversiones con y sin signo

Un tipo entero con signo y su homólogo sin signo son siempre del mismo tamaño, aunque difieren en cuanto a la forma de interpretar el patrón de bits para la transformación del valor. El ejemplo de código siguiente muestra lo que ocurre cuando el mismo patrón de bits se interpreta como valor con signo y como valor sin signo. El patrón de bits almacenado en `num` y `num2` nunca cambia respecto a lo que se muestra en la ilustración anterior.

```cpp
using namespace std;
unsigned short num = numeric_limits<unsigned short>::max(); // #include <limits>
short num2 = num;
cout << "unsigned val = " << num << " signed val = " << num2 << endl;
// Prints: unsigned val = 65535 signed val = -1

// Go the other way.
num2 = -1;
num = num2;
cout << "unsigned val = " << num << " signed val = " << num2 << endl;
// Prints: unsigned val = 65535 signed val = -1
```

Observe que los valores se reinterpretan en ambas direcciones. Si el programa produce resultados extraños en los que el signo del valor parece lo contrario de lo esperado, busque las conversiones implícitas entre los tipos enteros con y sin signo. In the following example, the result of the expression ( 0 - 1) is implicitly converted from **int** to **unsigned int** when it's stored in `num`. Esto hace que el patrón de bits se reinterprete.

```cpp
unsigned int u3 = 0 - 1;
cout << u3 << endl; // prints 4294967295
```

El compilador no advierte sobre las conversiones implícitas entre los tipos enteros con y sin signo. Por tanto, se recomienda evitar por completo las conversiones de tipos con signo a tipos sin signo. Si no puede evitarlas, agregue al código una comprobación en tiempo de ejecución para detectar si el valor que se está convirtiendo es mayor o igual que cero y menor o igual que el valor máximo del tipo con signo. Los valores de este intervalo se transferirán de tipos con signo a tipos sin signo, o viceversa, sin reinterpretaciones.

### <a name="pointer-conversions"></a>Conversiones de puntero

En muchas expresiones, una matriz de estilo C se convierte implícitamente a un puntero al primer elemento de la matriz y las conversiones de constantes pueden ocurrir de forma silenciosa. Aunque esto es conveniente, también es potencialmente propenso a errores. For example, the following badly designed code example seems nonsensical, and yet it will compile and produces a result of 'p'. Primero, el literal de la constante de cadena "Ayuda" se convierte en `char*`, que señala al primer elemento de la matriz; ese puntero se incrementa en tres elementos para que señale al último elemento "p".

```cpp
char* s = "Help" + 3;
```

## <a name="explicit-conversions-casts"></a>Conversiones explícitas

Mediante una operación de conversión, puede indicar al compilador que convierta un valor de un tipo a otro tipo. El compilador generará un error en algunos casos si los dos tipos no tienen ninguna relación entre sí, pero en otros casos no generará un error aunque la operación no tenga seguridad de tipos. Utilice las conversiones con moderación porque cualquier conversión de un tipo a otro es un origen potencial de errores del programa. Sin embargo, las conversiones son necesarias a veces y no todas son igualmente peligrosas. Una conversión se usa eficazmente cuando el código realiza una conversión de restricción y se sabe que la conversión no causará resultados incorrectos en el programa. En efecto, esto indica al compilador que sabe lo que está haciendo y que deje de molestarle con advertencias sobre ello. Otro uso es convertir desde una clase de puntero a derivado a una clase de puntero a base. Another use is to cast away the **const**-ness of a variable to pass it to a function that requires a non-**const** argument. La mayoría de estas operaciones de conversión implican algunos riesgos.

En la programación de estilo C, se utiliza el mismo operador de conversión de estilo C para todos los tipos de conversiones.

```cpp
(int) x; // old-style cast, old-style syntax
int(x); // old-style cast, functional syntax
```

El operador de conversión de estilo C es idéntico al operador de llamada () y, por consiguiente, no sobresale en el código y es sencillo pasarlo por alto. Both are bad because they're difficult to recognize at a glance or search for, and they're disparate enough to invoke any combination of **static**, **const**, and **reinterpret_cast**. Averiguar lo que hace realmente una conversión de estilo antiguo puede ser difícil y propenso a errores. Por todas estas razones, cuando se requiere una conversión, recomendamos utilizar uno de los siguientes operadores de conversión de C++, que en algunos casos tienen mucha más seguridad de tipos y expresan mucho más explícitamente la intención de la programación:

- **static_cast**, for casts that are checked at compile time only. **static_cast** returns an error if the compiler detects that you are trying to cast between types that are completely incompatible. También puede utilizarlo para convertir entre puntero a base y puntero a derivado, pero el compilador no puede determinar siempre si tales conversiones son seguras en tiempo de ejecución.

    ```cpp
    double d = 1.58947;
    int i = d;  // warning C4244 possible loss of data
    int j = static_cast<int>(d);       // No warning.
    string s = static_cast<string>(d); // Error C2440:cannot convert from
                                       // double to std:string

    // No error but not necessarily safe.
    Base* b = new Base();
    Derived* d2 = static_cast<Derived*>(b);
    ```

   For more information, see [static_cast](../cpp/static-cast-operator.md).

- **dynamic_cast**, for safe, runtime-checked casts of pointer-to-base to pointer-to-derived. A **dynamic_cast** is safer than a **static_cast** for downcasts, but the runtime check incurs some overhead.

    ```cpp
    Base* b = new Base();

    // Run-time check to determine whether b is actually a Derived*
    Derived* d3 = dynamic_cast<Derived*>(b);

    // If b was originally a Derived*, then d3 is a valid pointer.
    if(d3)
    {
       // Safe to call Derived method.
       cout << d3->DoSomethingMore() << endl;
    }
    else
    {
       // Run-time check failed.
       cout << "d3 is null" << endl;
    }

    //Output: d3 is null;
    ```

   For more information, see [dynamic_cast](../cpp/dynamic-cast-operator.md).

- **const_cast**, for casting away the **const**-ness of a variable, or converting a non-**const** variable to be **const**. Casting away **const**-ness by using this operator is just as error-prone as is using a C-style cast, except that with **const-cast** you are less likely to perform the cast accidentally. Sometimes you have to cast away the **const**-ness of a variable, for example, to pass a **const** variable to a function that takes a non-**const** parameter. En el ejemplo siguiente se muestra cómo hacerlo.

    ```cpp
    void Func(double& d) { ... }
    void ConstCast()
    {
       const double pi = 3.14;
       Func(const_cast<double&>(pi)); //No error.
    }
    ```

   For more information, see [const_cast](../cpp/const-cast-operator.md).

- **reinterpret_cast**, for casts between unrelated types such as **pointer** to **int**.

    > [!NOTE]
    >  Este operador de conversión no se usa tan a menudo como los demás y no se garantiza que sea portable a otros compiladores.

   The following example illustrates how **reinterpret_cast** differs from **static_cast**.

    ```cpp
    const char* str = "hello";
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot
                                  // convert from 'const char *' to 'int'
    int j = (int)str; // C-style cast. Did the programmer really intend
                      // to do this?
    int k = reinterpret_cast<int>(str);// Programming intent is clear.
                                       // However, it is not 64-bit safe.
    ```

   For more information, see [reinterpret_cast Operator](../cpp/reinterpret-cast-operator.md).

## <a name="see-also"></a>Vea también

[C++ type system](../cpp/cpp-type-system-modern-cpp.md)<br/>
[Welcome back to C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
