---
title: 'Operador and bit a bit: &amp;'
ms.date: 11/04/2016
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: ba17c9a633b7b18cad2881dfef90fde7c2074319
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446135"
---
# <a name="bitwise-and-operator-amp"></a>Operador and bit a bit: &amp;

## <a name="syntax"></a>Sintaxis

```
expression & expression
```

## <a name="remarks"></a>Observaciones

Las expresiones pueden ser otras expresiones de tipo and, o (en función de las restricciones de tipo que se mencionan más abajo), expresiones de igualdad, expresiones relacionales, expresiones aditivas, expresiones multiplicativas, expresiones de puntero a miembro, expresiones de conversión, expresiones unarias, expresiones de postfijo o expresiones primarias.

El operador and bit a bit ( **&** ) compara cada bit del primer operando con el bit correspondiente del segundo operando. Si ambos bits son 1, el bit de resultado correspondiente se establece en 1. De lo contrario, se establece en 0.

Ambos operandos para el operador AND bit a bit deben ser de tipos enteros. Las conversiones aritméticas habituales descritas en [conversiones estándar](standard-conversions.md)se aplican a los operandos.

## <a name="operator-keyword-for-"></a>Palabra clave del operador para &

El operador **BITAND** es el equivalente de texto de **&** . Hay dos maneras de tener acceso al operador **BITAND** en los programas: incluir el archivo de encabezado `iso646.h`o compilar con la opción del compilador [/za](../build/reference/za-ze-disable-language-extensions.md) (deshabilitar extensiones de lenguaje).

## <a name="example"></a>Ejemplo

```cpp
// expre_Bitwise_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise AND
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0xFFFF;      // pattern 1111 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...
}
```

## <a name="see-also"></a>Consulte también

[Operadores integrados de C++, precedencia y asociatividad](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores bit a bit de C](../c-language/c-bitwise-operators.md)