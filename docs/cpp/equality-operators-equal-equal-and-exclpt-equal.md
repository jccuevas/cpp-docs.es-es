---
title: 'Operadores de igualdad: == y !='
ms.date: 11/04/2016
f1_keywords:
- not_eq
- '!='
- ==
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: d6248d4a31c478b62e5fbe304d9bde9b51b7cb06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635648"
---
# <a name="equality-operators--and-"></a>Operadores de igualdad: == y !=

## <a name="syntax"></a>Sintaxis

```
expression == expression
expression != expression
```

## <a name="remarks"></a>Comentarios

Los operadores de igualdad binarios comparan la igualdad o desigualdad estricta de sus operandos.

Los operadores de igualdad, igual a (`==`) y no igual a (`!=`), tienen prioridad inferior que los operadores relacionales, pero se comportan de igual forma. Es el tipo de resultado de estos operadores **bool**.

El operador igual a (`==`) devuelve **true** (1) si ambos operandos tienen el mismo valor; en caso contrario, devuelve **false** (0). El operador no igual a (`!=`) devuelve **true** si los operandos no tienen el mismo valor; de lo contrario, devuelve **false**.

## <a name="operator-keyword-for-"></a>Palabra clave del operador para !=

El operador `not_eq` es el equivalente de texto de `!=`. Hay dos maneras de acceder a la `not_eq` operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).

## <a name="example"></a>Ejemplo

```cpp
// expre_Equality_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << boolalpha
         << "The true expression 3 != 2 yields: "
         << (3 != 2) << endl
         << "The false expression 20 == 10 yields: "
         << (20 == 10) << endl;
}
```

Los operadores de igualdad puede comparar punteros a miembros del mismo tipo. En esta comparación, se realizan las conversiones de puntero a miembro. Los punteros a miembros también se pueden comparar con una expresión constante que se evalúa como 0.

## <a name="see-also"></a>Vea también

[Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores relacionales y de igualdad de C](../c-language/c-relational-and-equality-operators.md)