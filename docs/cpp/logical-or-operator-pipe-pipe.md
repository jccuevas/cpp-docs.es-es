---
title: "Lógica u operador: || | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '||'
dev_langs:
- C++
helpviewer_keywords:
- OR operator, logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1784a3f0e7d069f7f7e2976fc7b71ea130d7c34b
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="logical-or-operator-"></a>Operador OR lógico: ||
## <a name="syntax"></a>Sintaxis  
  
```  
  
logical-or-expression   
||  
 logical-and-expression  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El operador lógico OR (`||`) devuelve el valor booleano **true** si uno o ambos operandos son **true** y devuelve **false** en caso contrario. Los operandos se convierten implícitamente al tipo `bool` antes de evaluación, y el resultado es de tipo `bool`. El operador OR lógico tiene asociatividad de izquierda a derecha.  
  
 Los operandos del operador OR lógico no tienen por qué ser del mismo tipo, pero deben ser de tipo entero o puntero. Los operandos son normalmente expresiones relacionales o de igualdad.  
  
 El primer operando se evalúa en su totalidad y, antes de proseguir con la evaluación de la expresión OR lógica, se aplican todos los efectos secundarios.  
  
 El segundo operando se evalúa solo si el primero se evalúa como false (0). Esto elimina la evaluación innecesaria del segundo operando cuando la expresión OR lógica es true.  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 En el ejemplo anterior, si `x` es igual a `w`, `y` o `z`, el segundo argumento de la función `printf` se evalúa como true y se imprime el valor 1. De lo contrario, se evalúa como false y se imprime el valor 0. En cuanto una de las condiciones se evalúe como true, se interrumpe la evaluación.  
  
## <a name="operator-keyword-for-124124"></a>Palabra clave del operador para &#124; &#124;  
 El **o** operador es el equivalente de texto de `||`. Hay dos maneras de obtener acceso a la **o** operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).  
  
## <a name="example"></a>Ejemplo  
  
```  
// expre_Logical_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical OR  
#include <iostream>  
using namespace std;  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b || b > c yields "  
         << (a < b || b > c) << endl  
         << "The false expression "  
         << "a > b || b > c yields "  
         << (a > b || b > c) << endl;  
}  
```  
  
## <a name="see-also"></a>Vea también  
[Los operadores integrados de C++ prioridad y asociatividad](cpp-built-in-operators-precedence-and-associativity.md) [operadores integrados de C++, prioridad y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores lógicos de C](../c-language/c-logical-operators.md)
