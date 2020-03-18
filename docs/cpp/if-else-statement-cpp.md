---
title: if-else (Instrucción) (C++)
ms.date: 07/20/2019
description: Use instrucciones IF-Else en C++ para controlar la bifurcación condicional.
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: 0e9de2d39e09e148c7e4f3ea82c3dadb173c2d0c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423775"
---
# <a name="if-else-statement-c"></a>if-else (Instrucción) (C++)

Controla la bifurcación condicional. Las instrucciones del *bloque if-* se ejecutan solo si la *expresión if-Expression* se evalúa como un valor distinto de cero (o true). Si el valor de *Expression* es distinto de cero, *instrucción1* y cualquier otra instrucción del bloque se ejecutan y el bloque else, si está presente, se omite. Si el valor de *Expression* es cero, el bloque if se omite y se ejecuta el bloque else, si está presente. Las expresiones que se evalúan como distintas de cero son

- TRUE
- un puntero no nulo,
- cualquier valor aritmético distinto de cero, o bien
- tipo de clase que define una conversión no ambigua a un tipo aritmético, booleano o de puntero. (Para obtener información sobre las conversiones, vea [conversiones estándar](../cpp/standard-conversions.md)).

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

// C++17 - Visual Studio 2017 version 15.3 and later:
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

// C++17 - Visual Studio 2017 version 15.3 and later:
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

## <a name="if_with_init"></a>instrucción If con un inicializador

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): una instrucción **If** también puede contener una expresión que declara e inicializa una variable con nombre. Utilice este formulario de la instrucción If-cuando la variable solo sea necesaria dentro del ámbito del bloque if.

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

En todas las formas de la instrucción **If** , se evalúa la *expresión*, que puede tener cualquier valor excepto una estructura, incluidos todos los efectos secundarios. El control pasa de la instrucción **If** a la siguiente instrucción del programa a menos que una de las *instrucciones*contenga [break](../cpp/break-statement-cpp.md), [continue](../cpp/continue-statement-cpp.md)o [goto](../cpp/goto-statement-cpp.md).

La cláusula **else** de una instrucción `if...else` está asociada a la instrucción **If** anterior más cercana en el mismo ámbito que no tiene una instrucción **else** correspondiente.

## <a name="a-nameif_constexpr-if-constexpr-statements"></a><a name="if_constexpr"> si las instrucciones constexpr

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): en las plantillas de función, puede usar una instrucción **If constexpr** para tomar decisiones de bifurcación en tiempo de compilación sin tener que recurrir a varias sobrecargas de función. Por ejemplo, puede escribir una función única que controle el desempaquetado de parámetros (no se necesita ninguna sobrecarga de parámetros cero):

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

## <a name="see-also"></a>Consulte también

[Instrucciones de selección](../cpp/selection-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[switch (Instrucción) (C++)](../cpp/switch-statement-cpp.md)