---
title: 'Operador lógico AND: &amp;&amp;'
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
ms.openlocfilehash: b21d91009c455b67af6fae88fceafeeaf8043301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179437"
---
# <a name="logical-and-operator-ampamp"></a>Operador lógico AND: &amp;&amp;

## <a name="syntax"></a>Sintaxis

```
expression && expression
```

## <a name="remarks"></a>Observaciones

El operador lógico AND ( **&&** ) devuelve el valor booleano true si ambos OPERANDOS son true y devuelve false en caso contrario. Los operandos se convierten implícitamente al tipo **bool** antes de la evaluación y el resultado es de tipo **bool**. El operador AND lógico tiene asociatividad de izquierda a derecha.

Los operandos del operador AND lógico no tienen por qué ser del mismo tipo, pero deben ser de tipo entero o puntero. Los operandos son normalmente expresiones relacionales o de igualdad.

El primer operando se evalúa en su totalidad y, antes de proseguir con la evaluación de la expresión AND lógica, se aplican todos los efectos secundarios.

El segundo operando solo se evalúa si el primero se evalúa como true (distinto de cero). Esta evaluación elimina la evaluación innecesaria del segundo operando cuando la expresión lógica AND es false. Puede utilizar esta evaluación de cortocircuito para evitar la desreferencia de punteros null, como se muestra en el ejemplo siguiente:

```cpp
char *pch = 0;
...
(pch) && (*pch = 'a');
```

Si `pch` es null (0), el lado derecho de la expresión no se evalúa. Por consiguiente, la asignación a través de un puntero null es imposible.

## <a name="operator-keyword-for-"></a>Palabra clave del operador para & &

El operador **and** es el equivalente de texto de **&&** . Hay dos maneras de tener acceso al operador **and** en los programas: incluir el archivo de encabezado `iso646.h`o compilar con la opción del compilador [/za](../build/reference/za-ze-disable-language-extensions.md) (deshabilitar extensiones de lenguaje).

## <a name="example"></a>Ejemplo

```cpp
// expre_Logical_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate logical AND
#include <iostream>

using namespace std;

int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b && b < c yields "
         << (a < b && b < c) << endl
         << "The false expression "
         << "a > b && b < c yields "
         << (a > b && b < c) << endl;
}
```

## <a name="see-also"></a>Consulte también

[C++Precedencia y asociatividad de los operadores integrados](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores lógicos de C](../c-language/c-logical-operators.md)
