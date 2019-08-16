---
title: 'Operador de llamada de función: ()'
ms.date: 11/04/2016
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
ms.openlocfilehash: 79c43ed11bfc73ec4bfaedad0a20b45fb6ca1ffb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154157"
---
# <a name="function-call-operator-"></a>Operador de llamada de función: ()

Una expresión de postfijo seguida del operador de llamada de función, **()**, especifica una llamada de función.

## <a name="syntax"></a>Sintaxis

```
postfix-expression
( [argument-expression-list ] )
```

## <a name="remarks"></a>Comentarios

Los argumentos del operador de llamada de función son cero o más expresiones separadas por comas (los argumentos reales de la función).

El *postfix-expression* debe evaluarse como una dirección de función (por ejemplo, un identificador de función o el valor de un puntero a función) y *argument-expression-list* es una lista de expresiones (separadas por comas) cuyos valores (los argumentos) se pasan a la función. El elemento *argument-expression-list* puede estar vacío.

El *postfix-expression* debe ser de uno de estos tipos:

- Una función que devuelve el tipo `T`. Una declaración de ejemplo es

    ```cpp
    T func( int i )
    ```

- Un puntero a una función que devuelve el tipo `T`. Una declaración de ejemplo es

    ```cpp
    T (*func)( int i )
    ```

- Una referencia a una función que devuelve el tipo `T`. Una declaración de ejemplo es

    ```cpp
    T (&func)(int i)
    ```

- Una desreferencia de función de puntero a miembro que devuelve el tipo `T`. Estos son algunos ejemplos de llamadas de función:

    ```cpp
    (pObject->*pmf)();
    (Object.*pmf)();
    ```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se llama a la función de biblioteca estándar `strcat_s` con tres argumentos:

```cpp
// expre_Function_Call_Operator.cpp
// compile with: /EHsc

#include <iostream>
#include <string>

// C++ Standard Library name space
using namespace std;

int main()
{
    enum
    {
        sizeOfBuffer = 20
    };

    char s1[ sizeOfBuffer ] = "Welcome to ";
    char s2[ ] = "C++";

    strcat_s( s1, sizeOfBuffer, s2 );

    cout << s1 << endl;
}
```

```Output
Welcome to C++
```

## <a name="function-call-results"></a>Resultados de la llamada de función

Una llamada de función se evalúa como un valor R a menos que la función se declare como un tipo de referencia. Las funciones con tipo de valor devuelto de referencia se evalúan como valores L y se pueden utilizar en el lado izquierdo de una instrucción de asignación, de la manera siguiente:

```cpp
// expre_Function_Call_Results.cpp
// compile with: /EHsc
#include <iostream>
class Point
{
public:
    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
private:
    unsigned _x;
    unsigned _y;
};

using namespace std;
int main()
{
    Point ThePoint;

    ThePoint.x() = 7;           // Use x() as an l-value.
    unsigned y = ThePoint.y();  // Use y() as an r-value.

    // Use x() and y() as r-values.
    cout << "x = " << ThePoint.x() << "\n"
         << "y = " << ThePoint.y() << "\n";
}
```

El código anterior define una clase denominada `Point`, que contiene los datos privados a objetos que representan *x* y *y* coordenadas. Estos objetos de datos se deben modificar y sus valores se deben recuperar. Este programa es solo uno de varios diseños para esa clase; el uso de las funciones `GetX` y `SetX` o `GetY` y `SetY` es otro diseño posible.

Las funciones que devuelven tipos de clase, punteros a tipos de clase o referencias a tipos de clase se pueden utilizar como operando izquierdo para operadores de selección de miembros. Por consiguiente, el código siguiente es legal.

```cpp
// expre_Function_Results2.cpp
class A {
public:
   A() {}
   A(int i) {}
   int SetA( int i ) {
      return (I = i);
   }

   int GetA() {
      return I;
   }

private:
   int I;
};

A func1() {
   A a = 0;
   return a;
}

A* func2() {
   A *a = new A();
   return a;
}

A& func3() {
   A *a = new A();
   A &b = *a;
   return b;
}

int main() {
   int iResult = func1().GetA();
   func2()->SetA( 3 );
   func3().SetA( 7 );
}
```

Las funciones se pueden llamar de forma recursiva. Para obtener más información acerca de las declaraciones de función, vea [funciones](functions-cpp.md). Material relacionado está en [programa y vinculación](../cpp/program-and-linkage-cpp.md).

## <a name="see-also"></a>Vea también

[Expresiones postfijas](../cpp/postfix-expressions.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Llamada a función](../c-language/function-call-c.md)