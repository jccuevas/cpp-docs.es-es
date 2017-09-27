---
title: "Operador AND lógico: &amp; &amp; | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '&&'
dev_langs:
- C++
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
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
ms.openlocfilehash: 5a594efcc987fba69ceb17e7e09d10470adab75f
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="logical-and-operator-ampamp"></a>Operador AND lógico:&amp;&amp;
## <a name="syntax"></a>Sintaxis  
  
```  
  
expression   
&&  
 expression  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El operador lógico AND (**&&**) devuelve el valor booleano **true** si ambos operandos son **true** y devuelve **false** en caso contrario. Los operandos se convierten implícitamente al tipo `bool` antes de evaluación, y el resultado es de tipo `bool`. El operador AND lógico tiene asociatividad de izquierda a derecha.  
  
 Los operandos del operador AND lógico no tienen por qué ser del mismo tipo, pero deben ser de tipo entero o puntero. Los operandos son normalmente expresiones relacionales o de igualdad.  
  
 El primer operando se evalúa en su totalidad y, antes de proseguir con la evaluación de la expresión AND lógica, se aplican todos los efectos secundarios.  
  
 El segundo operando solo se evalúa si el primero se evalúa como true (distinto de cero). Esta evaluación elimina la evaluación innecesaria del segundo operando cuando la expresión lógica AND es false. Puede utilizar esta evaluación de cortocircuito para evitar la desreferencia de punteros null, como se muestra en el ejemplo siguiente:  
  
```  
char *pch = 0;  
...  
(pch) && (*pch = 'a');  
```  
  
 Si `pch` es null (0), el lado derecho de la expresión no se evalúa. Por consiguiente, la asignación a través de un puntero null es imposible.  
  
## <a name="operator-keyword-for-"></a>Palabra clave del operador para &&  
 El **y** operador es el equivalente de texto de ** && **. Hay dos maneras de obtener acceso a la **y** operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).  
  
## <a name="example"></a>Ejemplo  
  
```  
// expre_Logical_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical AND  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b && b < c yields "  
         << (a < b && b < c) << endl  
         << "The false expression "  
         << "a > b && b < c yields "  
         << (a > b && b < c) << endl;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Los operadores integrados de C++ prioridad y asociatividad](cpp-built-in-operators-precedence-and-associativity.md) [operadores integrados de C++, prioridad y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores lógicos de C](../c-language/c-logical-operators.md)
