---
title: if-else (Instrucción) (C++)
ms.date: 07/17/2017
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
- if keyword [C++], if-else
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: a6ab56befb4416bf232109a63932604e256df639
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471427"
---
# <a name="if-else-statement-c"></a>if-else (Instrucción) (C++)

Controla la bifurcación condicional. Las instrucciones de la *bloques if* se ejecutan solo si el *expresión if* se evalúa como un valor distinto de cero (o TRUE). Si el valor de *expresión* es distinto de cero, *statement1* y cualquier otra instrucción en el bloque se ejecutan y el bloque-else, si está presente, se omite. Si el valor de *expresión* es cero, a continuación, se omite el bloque if y el bloque-else, si está presente, se ejecuta. Son expresiones que se evalúan como distinto de cero

- true
- un puntero no null,
- cualquier valor distinto de cero aritmético, o
- Escriba un tipo de clase que define una conversión no ambigua a una aritmética, booleano o de puntero. (Para obtener información sobre las conversiones, vea [conversiones estándar](../cpp/standard-conversions.md).)

## <a name="syntax"></a>Sintaxis

```cpp
if ( expression )
{
   statement1;
   ...
}
else  // optional
{
   statement2;
   ...
}

// Visual Studio 2017 version 15.3 and later:
if ( initialization; expression )
{
   statement1;
   ...
}
else  // optional
{
   statement2;
   ...
}

// Visual Studio 2017 version 15.3 and later:
if constexpr (expression)
{
    statement1;
    ...
}
else  // optional
{
   statement2;
   ...
}
```

## <a name="example"></a>Ejemplo

```cpp
// if_else_statement.cpp
#include <iostream>

using namespace std;

class C
{
    public:
    void do_something(){}
};
void init(C){}
bool is_true() { return true; }
int x = 10;

int main()
{
    if (is_true())
    {
        cout << "b is true!\n";  // executed
    }
    else
    {
        cout << "b is false!\n";
    }

    // no else statement
    if (x == 10)
    {
        x = 0;
    }

    C* c;
    init(c);
    if (c)
    {
        c->do_something();
    }
    else
    {
        cout << "c is null!\n";
    }
}
```

## <a name="if_with_init"></a> Si la instrucción con un inicializador

**Visual Studio 2017 versión 15.3 y versiones posterior** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): un **si** instrucción también puede contener una expresión que se declara e inicializa una variable con nombre. Utilice este formulario de la instrucción if cuando la variable solo es necesario dentro del ámbito del bloque de if.

## <a name="example"></a>Ejemplo

```cpp
#include <iostream>
#include <mutex>
#include <map>
#include <string>
#include <algorithm>

using namespace std;

map<int, string> m;
mutex mx;
bool shared_flag; // guarded by mx
void unsafe_operation() {}

int main()
{

    if (auto it = m.find(10); it != m.end())
    {
        cout << it->second;
        return 0;
    }

    if (char buf[10]; fgets(buf, 10, stdin))
    {
        m[0] += buf;
    }

    if (lock_guard<mutex> lock(mx); shared_flag)
    {
        unsafe_operation();
        shared_flag = false;
    }

    string s{ "if" };
    if (auto keywords = { "if", "for", "while" }; any_of(keywords.begin(), keywords.end(), [&s](const char* kw) { return s == kw; }))
    {
        cout << "Error! Token must not be a keyword\n";
    }
}
```

En todos los formularios de la **si** instrucción, *expresión*, que puede tener cualquier valor excepto una estructura, se evalúa, incluidos todos los efectos. Control pasa de la **si** instrucción a la siguiente instrucción en el programa a menos que uno de los *instrucción*s contiene un [salto](../cpp/break-statement-cpp.md), [continuar](../cpp/continue-statement-cpp.md), o [goto](../cpp/goto-statement-cpp.md).

El **else** cláusula de una `if...else` instrucción está asociada con el más cercano anterior **si** instrucción en el mismo ámbito que no tiene la correspondiente **else** instrucción.

## <a name="a-nameifconstexpr-if-constexpr-statements"></a><a name="if_constexpr"> Si las instrucciones de constexpr

**Visual Studio 2017 versión 15.3 y versiones posterior** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): en las plantillas de función, puede usar un **si constexpr** instrucción para tomar decisiones de bifurcación de tiempo de compilación sin tener que recurrir a varias sobrecargas de función. Por ejemplo, puede escribir una sola función ese parámetro de identificadores para desempaquetar (no se necesita ninguna sobrecarga de parámetro de cero):

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
    // handle t
    do_something(t);

    // handle r conditionally
    if constexpr (sizeof...(r))
    {
        f(r...);
    }
    else
    {
        g(r...);
    }
}
```

## <a name="see-also"></a>Vea también

[Instrucciones de selección](../cpp/selection-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[switch (Instrucción) (C++)](../cpp/switch-statement-cpp.md)