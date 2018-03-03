---
title: 'Uno &#39; s operador de complemento: ~ | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ~
dev_langs:
- C++
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 635a3e3b2d270d2164adc3f25a260085d7c50d60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="one39s-complement-operator-"></a>Uno &#39; s operador de complemento: ~
## <a name="syntax"></a>Sintaxis  
  
```  
  
~ cast-expression  
```  
  
## <a name="remarks"></a>Comentarios  
 El operador de complemento de uno (`~`), denominado a veces operador de “complemento bit a bit”, produce un complemento de uno bit a bit de su operando. Es decir, cada bit que es 1 en el operando es 0 en el resultado. Y a la inversa: cada bit que es 0 en el operando es 1 en el resultado. El operando del operador de complemento de uno debe ser de tipo entero.  
  
## <a name="operator-keyword-for-"></a>Palabra clave del operador para ~  
 El operador `compl` es el equivalente de texto de `~`. Hay dos maneras de obtener acceso a la `compl` operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con [/Za](../build/reference/za-ze-disable-language-extensions.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
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
  
 La promoción de entero se realiza en operandos enteros y el tipo resultante es el tipo al que se promueve el operando. Vea [conversiones estándar](standard-conversions.md) para obtener más información sobre cómo se realiza la promoción.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Los operadores integrados de C++, prioridad y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores aritméticos unarios](../c-language/unary-arithmetic-operators.md)