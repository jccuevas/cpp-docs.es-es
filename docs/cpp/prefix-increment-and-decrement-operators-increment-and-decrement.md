---
title: 'Operadores de incremento y decremento prefijos: ++ y --'
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
ms.openlocfilehash: 32c210961c4966bb7b2cbcc597bd3c99f0d6ed24
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177669"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Operadores de incremento y decremento prefijos: ++ y --

## <a name="syntax"></a>Sintaxis

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Observaciones

El operador de incremento de prefijo ( **++** ) agrega uno a su operando; Este valor incrementado es el resultado de la expresión. El operando debe ser un valor l que no sea de tipo **const**. El resultado es un valor L del mismo tipo que el operando.

El operador de decremento de prefijo ( **--** ) es análogo al operador de incremento de prefijo, salvo que el operando se reduce en uno y el resultado es este valor disminuido.

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): el operando de un operador de incremento o decremento no puede ser de tipo **bool**.

Los operadores de incremento y decremento de prefijo y postfijo afectan a sus operandos. La principal diferencia entre ellos es el orden en que se realiza el incremento o el decremento al evaluar una expresión. (Para obtener más información, vea [operadores de incremento y decremento postfijo](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)). En el formato de prefijo, el incremento o decremento tiene lugar antes de que el valor se use en la evaluación de la expresión, por lo que el valor de la expresión es diferente del valor del operando. En la forma de postfijo, el incremento o decremento tiene lugar después de que el valor se use en la evaluación de la expresión, por lo que el valor de la expresión es el mismo que el valor del operando. Por ejemplo, el siguiente programa imprime “`++i = 6`”:

```cpp
// expre_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   int i = 5;
   cout << "++i = " << ++i << endl;
}
```

Un operando de tipo entero o flotante aumenta o disminuye en el valor entero 1. El tipo del resultado es el mismo que el tipo del operando. Un operando de tipo de puntero aumenta o disminuye en el tamaño del objeto al que apunta. Un puntero incrementado apunta al siguiente objeto; un puntero disminuido apunta al objeto anterior.

Dado que los operadores de incremento y decremento tienen efectos secundarios, el uso de expresiones con operadores de incremento o decremento en una [macro de preprocesador](../preprocessor/macros-c-cpp.md) puede tener resultados no deseados. En este ejemplo:

```cpp
// expre_Increment_and_Decrement_Operators2.cpp
#define max(a,b) ((a)<(b))?(b):(a)

int main()
{
   int i = 0, j = 0, k;
   k = max( ++i, j );
}
```

La macro se expande en:

```cpp
k = ((++i)<(j))?(j):(++i);
```

Si `i` es mayor o igual que `j` o es menor que `j` en 1, aumentará dos veces.

> [!NOTE]
>  Las funciones insertadas de C++ son preferibles a las macros en muchos casos porque eliminan los efectos secundarios como los que se describen aquí, y permiten que el lenguaje realice una comprobación de tipos más completa.

## <a name="see-also"></a>Consulte también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores de incremento y decremento prefijos](../c-language/prefix-increment-and-decrement-operators.md)
