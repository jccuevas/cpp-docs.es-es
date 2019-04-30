---
title: 'Operador lógico OR: ||'
ms.date: 06/14/2018
f1_keywords:
- '||'
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 5db1af870644d1552aeac813edce0985a31d95b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368687"
---
# <a name="logical-or-operator-"></a>Operador lógico OR: ||

## <a name="syntax"></a>Sintaxis

> *logical-or-expression* **||** *logical-and-expression*

## <a name="remarks"></a>Comentarios

El operador lógico OR (**||**) devuelve el valor booleano TRUE si uno o ambos operandos es TRUE y devuelve FALSE en caso contrario. Los operandos se convierten implícitamente al tipo **bool** antes de la evaluación y el resultado es de tipo **bool**. El operador OR lógico tiene asociatividad de izquierda a derecha.

Los operandos del operador OR lógico no tienen por qué ser del mismo tipo, pero deben ser de tipo entero o puntero. Los operandos son normalmente expresiones relacionales o de igualdad.

El primer operando se evalúa en su totalidad y, antes de proseguir con la evaluación de la expresión OR lógica, se aplican todos los efectos secundarios.

El segundo operando se evalúa solo si el primero se evalúa como false (0). Esto elimina la evaluación innecesaria del segundo operando cuando la expresión OR lógica es true.

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

En el ejemplo anterior, si `x` es igual a `w`, `y` o `z`, el segundo argumento de la función `printf` se evalúa como true y se imprime el valor 1. De lo contrario, se evalúa como false y se imprime el valor 0. En cuanto una de las condiciones se evalúe como true, se interrumpe la evaluación.

## <a name="operator-keyword-for-124124"></a>Palabra clave del operador para&#124;&#124;

El **o** operador es el equivalente textual de **||**. Hay dos maneras de acceder a la **o** operador en los programas: incluir el archivo de encabezado \<iso646.h >, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).

## <a name="example"></a>Ejemplo

```cpp
// expre_Logical_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate logical OR
#include <iostream>
using namespace std;
int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b || b > c yields "
         << (a < b || b > c) << endl
         << "The false expression "
         << "a > b || b > c yields "
         << (a > b || b > c) << endl;
}
```

## <a name="see-also"></a>Vea también

[Operadores integrados de C++ prioridad y asociatividad](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores lógicos de C](../c-language/c-logical-operators.md)