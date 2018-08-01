---
title: 'Bit a bit operador OR inclusivo: || Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bitor
- '|'
dev_langs:
- C++
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75cb922f2bd5cc6da2666a59bd0827b7ec013bf2
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409440"
---
# <a name="bitwise-inclusive-or-operator-"></a>Bit a bit operador OR inclusivo: |

## <a name="syntax"></a>Sintaxis

> *expression1* **|** *expression2*

## <a name="remarks"></a>Comentarios

El operador OR inclusivo bit a bit (**&#124;**) compara cada bit del primer operando con el bit correspondiente del segundo operando. Si uno de los dos bits es 1, el bit del resultado correspondiente se establece en 1. De lo contrario, el bit del resultado correspondiente se establece en 0.

Ambos operandos del operador OR inclusivo bit a bit deben ser de tipos enteros. Tratan las conversiones aritméticas habituales en [conversiones estándar](standard-conversions.md) se aplican a los operandos.

## <a name="operator-keyword-for-124"></a>Palabra clave del operador para&#124;

El **bitor** operador es el equivalente textual de **&#124;**. Hay dos maneras de acceder a la **bitor** operador en los programas: incluir el archivo de encabezado \<iso646.h >, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).

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

## <a name="see-also"></a>Vea también
 [Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
 [Operadores bit a bit de C](../c-language/c-bitwise-operators.md)  