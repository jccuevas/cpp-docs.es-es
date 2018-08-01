---
title: 'Operador AND bit a bit: &amp; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bitand
dev_langs:
- C++
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3122cb3622469adeda3b8c0a2437fe4db7dfca62
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404218"
---
# <a name="bitwise-and-operator-amp"></a>Operador AND bit a bit: &amp;

## <a name="syntax"></a>Sintaxis  
  
```
expression & expression  
```
  
## <a name="remarks"></a>Comentarios  
 Las expresiones pueden ser otras expresiones de tipo and, o (en función de las restricciones de tipo que se mencionan más abajo), expresiones de igualdad, expresiones relacionales, expresiones aditivas, expresiones multiplicativas, expresiones de puntero a miembro, expresiones de conversión, expresiones unarias, expresiones de postfijo o expresiones primarias.  
  
 El operador AND bit a bit (**&**) compara cada bit del primer operando con el bit correspondiente del segundo operando. Si ambos bits son 1, el bit del resultado correspondiente se establece en 1. De lo contrario, el bit del resultado correspondiente se establece en 0.  
  
 Ambos operandos para el operador AND bit a bit deben ser de tipos enteros. Tratan las conversiones aritméticas habituales en [conversiones estándar](standard-conversions.md), se aplican a los operandos.  
  
## <a name="operator-keyword-for-"></a>Palabra clave del operador para &  
 El **bitand** operador es el equivalente textual de **&**. Hay dos maneras de acceder a la **bitand** operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).  
  
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
  
## <a name="see-also"></a>Vea también  
 [Operadores integrados de C++, precedencia y asociatividad](cpp-built-in-operators-precedence-and-associativity.md)  
 [Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores bit a bit de C](../c-language/c-bitwise-operators.md)