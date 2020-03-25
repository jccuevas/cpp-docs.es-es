---
title: 'Operador OR lógico: ||'
ms.date: 06/14/2018
f1_keywords:
- '||'
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 94b2bc024dd7223ac7adacc72924f5ee289bab37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178085"
---
# <a name="logical-or-operator-"></a>Operador OR lógico: ||

## <a name="syntax"></a>Sintaxis

> *Logical-or-expression* **||** *Logical-and-Expression*

## <a name="remarks"></a>Observaciones

El operador lógico OR ( **||** ) devuelve el valor booleano true si uno o ambos OPERANDOS son true y devuelve false en caso contrario. Los operandos se convierten implícitamente al tipo **bool** antes de la evaluación y el resultado es de tipo **bool**. El operador OR lógico tiene asociatividad de izquierda a derecha.

Los operandos del operador OR lógico no tienen por qué ser del mismo tipo, pero deben ser de tipo entero o puntero. Los operandos son normalmente expresiones relacionales o de igualdad.

El primer operando se evalúa en su totalidad y, antes de proseguir con la evaluación de la expresión OR lógica, se aplican todos los efectos secundarios.

El segundo operando se evalúa solo si el primero se evalúa como false (0). Esto elimina la evaluación innecesaria del segundo operando cuando la expresión OR lógica es true.

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

En el ejemplo anterior, si `x` es igual a `w`, `y` o `z`, el segundo argumento de la función `printf` se evalúa como true y se imprime el valor 1. De lo contrario, se evalúa como false y se imprime el valor 0. En cuanto una de las condiciones se evalúe como true, se interrumpe la evaluación.

## <a name="operator-keyword-for-124124"></a>Operator (palabra clave) para&#124;&#124;

El operador **or** es el equivalente de texto de **||** . Hay dos maneras de tener acceso al operador **or** en los programas: incluir el archivo de encabezado \<iso646. h > o compilar con la opción del compilador [/za](../build/reference/za-ze-disable-language-extensions.md) (deshabilitar extensiones de lenguaje).

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

## <a name="see-also"></a>Consulte también

[C++Precedencia y asociatividad de los operadores integrados](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores lógicos de C](../c-language/c-logical-operators.md)
