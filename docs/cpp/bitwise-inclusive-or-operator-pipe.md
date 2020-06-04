---
title: 'Operador OR inclusivo bit a bit: |'
ms.date: 06/14/2018
f1_keywords:
- '|'
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 38def2b1ac585c751699227d2a065b45145d290d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190760"
---
# <a name="bitwise-inclusive-or-operator-"></a>Operador OR inclusivo bit a bit: |

## <a name="syntax"></a>Sintaxis

> *expression1* **|** *expresión2*

## <a name="remarks"></a>Observaciones

El operador OR inclusivo bit **&#124;** a bit () compara cada bit de su primer operando con el bit correspondiente de su segundo operando. Si cualquiera de los bits es 1, el bit de resultado correspondiente se establece en 1. De lo contrario, se establece en 0.

Ambos operandos del operador OR inclusivo bit a bit deben ser de tipos enteros. Las conversiones aritméticas habituales descritas en [conversiones estándar](standard-conversions.md) se aplican a los operandos.

## <a name="operator-keyword-for-124"></a>Operator (palabra clave) para&#124;

El operador **BITOR** es el equivalente de texto **&#124;** de. Hay dos maneras de tener acceso al operador **BITOR** en los programas: incluir el archivo de encabezado \<iso646. h > o compilar con la opción del compilador [/za](../build/reference/za-ze-disable-language-extensions.md) (deshabilitar extensiones de lenguaje).

## <a name="example"></a>Ejemplo

```cpp
// expre_Bitwise_Inclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise inclusive OR
#include <iostream>
using namespace std;

int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...
}
```

## <a name="see-also"></a>Consulte también

[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores bit a bit de C](../c-language/c-bitwise-operators.md)
