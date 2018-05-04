---
title: 'Operador OR exclusivo bit a bit: ^ | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d080fa28e8f70cb6a4086709c4a5fc6215c4519
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="bitwise-exclusive-or-operator-"></a>Operador OR exclusivo bit a bit: ^
## <a name="syntax"></a>Sintaxis  
  
```  
expression ^ expression  
```  
  
## <a name="remarks"></a>Comentarios  
El operador OR exclusivo bit a bit (**^**) compara cada bit del primer operando con el bit correspondiente de su segundo operando. Si un bit es 0 y el otro bit es 1, el bit del resultado correspondiente se establece en 1. De lo contrario, el bit del resultado correspondiente se establece en 0.  
  
Ambos operandos del operador OR exclusivo bit a bit deben ser de tipos enteros. Las conversiones aritméticas habituales descritas en [conversiones estándar](standard-conversions.md) se aplican a los operandos.  
  
## <a name="operator-keyword-for-"></a>Palabra clave de operador para ^  
El **xor** operador es el equivalente de texto de **^**. Hay dos maneras de obtener acceso a la **xor** operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).  
  
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
  
## <a name="see-also"></a>Vea también  
 [Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   


