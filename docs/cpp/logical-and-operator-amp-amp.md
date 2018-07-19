---
title: 'Operador AND lógico: &amp; &amp; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d826ba5a2252ba11a0b9206a0555c7a022a9382c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944685"
---
# <a name="logical-and-operator-ampamp"></a>Operador lógico AND: &amp;&amp;
## <a name="syntax"></a>Sintaxis  
  
```  
  
expression && expression  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El operador lógico AND (**&&**) devuelve el valor booleano TRUE si ambos operandos son TRUE y FALSE en caso contrario. Los operandos se convierten implícitamente al tipo **bool** antes de la evaluación y el resultado es de tipo **bool**. El operador AND lógico tiene asociatividad de izquierda a derecha.  
  
 Los operandos del operador AND lógico no tienen por qué ser del mismo tipo, pero deben ser de tipo entero o puntero. Los operandos son normalmente expresiones relacionales o de igualdad.  
  
 El primer operando se evalúa en su totalidad y, antes de proseguir con la evaluación de la expresión AND lógica, se aplican todos los efectos secundarios.  
  
 El segundo operando solo se evalúa si el primero se evalúa como true (distinto de cero). Esta evaluación elimina la evaluación innecesaria del segundo operando cuando la expresión lógica AND es false. Puede utilizar esta evaluación de cortocircuito para evitar la desreferencia de punteros null, como se muestra en el ejemplo siguiente:  
  
```cpp 
char *pch = 0;  
...  
(pch) && (*pch = 'a');  
```  
  
 Si `pch` es null (0), el lado derecho de la expresión no se evalúa. Por consiguiente, la asignación a través de un puntero null es imposible.  
  
## <a name="operator-keyword-for-"></a>Palabra clave del operador para &&  
 El **y** operador es el equivalente textual de **&&**. Hay dos maneras de acceder a la **y** operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
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
 [Operadores integrados de C++ prioridad y asociatividad](cpp-built-in-operators-precedence-and-associativity.md) [operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores lógicos de C](../c-language/c-logical-operators.md)