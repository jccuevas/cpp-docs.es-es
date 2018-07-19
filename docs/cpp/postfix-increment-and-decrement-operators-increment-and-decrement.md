---
title: 'Operadores de incremento y decremento de postfijo: ++ y--| Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- C++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e6021de0e012797b811fa032547f2b95142176cc
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944516"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>Operadores de incremento y decremento postfijos: ++ y --
## <a name="syntax"></a>Sintaxis  
  
```  
postfix-expression ++  
postfix-expression --  
```  
  
## <a name="remarks"></a>Comentarios  
 C++ proporciona operadores de incremento y decremento tanto de prefijo como de postfijo. En esta sección, se describen solo los de postfijo. (Para obtener más información, consulte [prefijo operadores de incremento y decremento](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md).) La diferencia entre los dos es que en la notación de postfijo, el operador aparece después de *postfix-expression*, mientras que en la notación de prefijo, el operador aparece antes de *expresión.* En el ejemplo siguiente, se muestra un operador de incremento de postfijo:  
  
```cpp 
i++;  
```  
  
 La aplicación del operador de incremento de postfijo (`++`) tiene como efecto que el valor del operando se incrementa en una unidad del tipo adecuado. De forma similar, el efecto de aplicar el operador de decremento de postfijo (**--**) es que el valor del operando se reduce en una unidad del tipo adecuado.  
  
 Es importante tener en cuenta que se incremente un sufijo o decremento expresión se evalúa como el valor de la expresión *anteriores a* de aplicar el operador correspondiente. Se produce la operación de incremento o decremento *después* el operando se evalúa. El problema surge solo cuando la operación de incremento o decremento de postfijo se da en el contexto de una expresión mayor.  
  
 Cuando se aplica un operador de postfijo a un argumento de función, no es seguro que el valor del argumento aumente o disminuya antes de que se pase a la función.  Para obtener más información, vea la sección 1.9.17 del estándar C++.  
  
 Aplicar el operador de incremento de postfijo a un puntero a una matriz de objetos de tipo **largo** realmente se agregan cuatro a la representación interna del puntero. Este comportamiento hace que el puntero, que anteriormente se hacía referencia a la *n*elemento de la matriz, para hacer referencia a la (*n*+ 1) elemento th.  
  
 Los operandos e incremento de operadores de decremento de postfijo deben ser modificables (no **const**) valores l de tipo aritmético o puntero. El tipo del resultado es el mismo que el de la *postfix-expression*, pero ya no es un valor l.  
  
**Visual Studio 2017 versión 15.3 y versiones posterior** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): el operando de un postfijo de incremento o decremento operador no puede ser de tipo **bool**.
  
 El código siguiente muestra el operador de incremento de postfijo:  
  
```cpp 
// expre_Postfix_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 10;  
   cout << i++ << endl;  
   cout << i << endl;  
}  
```  
  
 No se admiten las operaciones de incremento y decremento de postfijo en los tipos enumerados:  
  
```cpp 
enum Compass { North, South, East, West );  
Compass myCompass;  
for( myCompass = North; myCompass != West; myCompass++ ) // Error  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones de postfijo](../cpp/postfix-expressions.md)   
 [Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores de incremento y decremento postfijos de C](../c-language/c-postfix-increment-and-decrement-operators.md)