---
title: 'Bit a bit inclusivo u operador: || Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bitor
- '|'
dev_langs: C++
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 792a5ef5576f68925459d8e7a34168afa11871c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="bitwise-inclusive-or-operator-"></a>Operador OR inclusivo bit a bit: |
## <a name="syntax"></a>Sintaxis  
  
```  
  
expression   
|  
 expression  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El operador OR inclusivo bit a bit (**&#124;**) compara cada bit del primer operando con el bit correspondiente de su segundo operando. Si uno de los dos bits es 1, el bit del resultado correspondiente se establece en 1. De lo contrario, el bit del resultado correspondiente se establece en 0.  
  
 Ambos operandos del operador OR inclusivo bit a bit deben ser de tipos enteros. Las conversiones aritméticas habituales descritas en [conversiones estándar](standard-conversions.md) se aplican a los operandos.  
  
## <a name="operator-keyword-for-124"></a>Palabra clave del operador para &#124;  
 El `bitor` operador es el equivalente de texto de **&#124;**. Hay dos maneras de obtener acceso a la `bitor` operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).  
  
## <a name="example"></a>Ejemplo  
  
```  
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
 [Los operadores integrados de C++, prioridad y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores bit a bit de C](../c-language/c-bitwise-operators.md)

