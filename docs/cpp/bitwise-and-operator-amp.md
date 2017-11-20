---
title: 'Operador AND bit a bit: &amp; | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: bitand
dev_langs: C++
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2bf6369e0404705d84533778357f7fe339c7ef55
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="bitwise-and-operator-amp"></a>Operador AND bit a bit:&amp;
## <a name="syntax"></a>Sintaxis  
  
```  
  
expression   
&  
 expression  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Las expresiones pueden ser otras expresiones de tipo and, o (en función de las restricciones de tipo que se mencionan más abajo), expresiones de igualdad, expresiones relacionales, expresiones aditivas, expresiones multiplicativas, expresiones de puntero a miembro, expresiones de conversión, expresiones unarias, expresiones de postfijo o expresiones primarias.  
  
 El operador AND bit a bit (**&**) compara cada bit del primer operando con el bit correspondiente del segundo operando. Si ambos bits son 1, el bit del resultado correspondiente se establece en 1. De lo contrario, el bit del resultado correspondiente se establece en 0.  
  
 Ambos operandos para el operador AND bit a bit deben ser de tipos enteros. Las conversiones aritméticas habituales descritas en [conversiones estándar](standard-conversions.md), se aplican a los operandos.  
  
## <a name="operator-keyword-for-"></a>Palabra clave del operador para &  
 El `bitand` operador es el equivalente de texto de  **&** . Hay dos maneras de obtener acceso a la `bitand` operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).  
  
## <a name="example"></a>Ejemplo  
  
```  
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
 [Los operadores integrados de C++, prioridad y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores bit a bit de C](../c-language/c-bitwise-operators.md)