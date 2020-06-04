---
title: 'Operador&#39;de complemento de uno: ~'
ms.date: 11/04/2016
f1_keywords:
- "~"
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: 777f253925caf38647863bdaa93fde8d5a03e3f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177721"
---
# <a name="one39s-complement-operator-"></a>Operador&#39;de complemento de uno: ~

## <a name="syntax"></a>Sintaxis

```
~ cast-expression
```

## <a name="remarks"></a>Observaciones

El operador de complemento de uno (`~`), denominado a veces operador de “complemento bit a bit”, produce un complemento de uno bit a bit de su operando. Es decir, cada bit que es 1 en el operando es 0 en el resultado. Y a la inversa: cada bit que es 0 en el operando es 1 en el resultado. El operando del operador de complemento de uno debe ser de tipo entero.

## <a name="operator-keyword-for-"></a>Palabra clave del operador para ~

El operador **compl** es el equivalente de texto de `~`. Hay dos maneras de tener acceso al operador **compl** en los programas: incluir el archivo de encabezado `iso646.h`o compilar con [/za](../build/reference/za-ze-disable-language-extensions.md).

## <a name="example"></a>Ejemplo

```cpp
// expre_One_Complement_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main () {
   unsigned short y = 0xFFFF;
   cout << hex << y << endl;
   y = ~y;   // Take one's complement
   cout << hex << y << endl;
}
```

En este ejemplo, el nuevo valor asignado a `y` es el complemento de uno del valor sin signo 0xFFFF, or 0x0000.

La promoción de entero se realiza en operandos enteros y el tipo resultante es el tipo al que se promueve el operando. Consulte [conversiones estándar](standard-conversions.md) para obtener más información sobre cómo se realiza la promoción.

## <a name="see-also"></a>Consulte también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores aritméticos unarios](../c-language/unary-arithmetic-operators.md)
