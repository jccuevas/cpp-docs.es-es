---
title: 'Operador OR exclusivo bit a bit: ^'
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 9a44dc60a985729aae79ed0e2e48c44adace647b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190721"
---
# <a name="bitwise-exclusive-or-operator-"></a>Operador OR exclusivo bit a bit: ^

## <a name="syntax"></a>Sintaxis

```
expression ^ expression
```

## <a name="remarks"></a>Observaciones

El operador OR exclusivo bit a bit ( **^** ) compara cada bit de su primer operando con el bit correspondiente de su segundo operando. Si un bit es 0 y el otro bit es 1, el bit de resultado correspondiente se establece en 1. De lo contrario, se establece en 0.

Ambos operandos del operador OR exclusivo bit a bit deben ser de tipos enteros. Las conversiones aritméticas habituales descritas en [conversiones estándar](standard-conversions.md) se aplican a los operandos.

## <a name="operator-keyword-for-"></a>Palabra clave de operador para ^

El operador **XOR** es el equivalente de texto de **^** . Hay dos maneras de tener acceso al operador **XOR** en los programas: incluir el archivo de encabezado `iso646.h`o compilar con la opción del compilador [/za](../build/reference/za-ze-disable-language-extensions.md) (deshabilitar extensiones de lenguaje).

## <a name="example"></a>Ejemplo

```cpp
// expre_Bitwise_Exclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise exclusive OR
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xFFFF;      // pattern 1111 ...

   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...
}
```

## <a name="see-also"></a>Consulte también

[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
