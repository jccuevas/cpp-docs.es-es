---
title: "Operador lógico de negación: ! | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '!'
- Not
dev_langs:
- C++
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 42d6135ab442a6f158fddd4ebfec1ef669fdecfd
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="logical-negation-operator-"></a>Operador lógico de negación: !
## <a name="syntax"></a>Sintaxis  
  
```  
  
! cast-expression  
```  
  
## <a name="remarks"></a>Comentarios  
 El operador de negación lógica (**!**) invierte el significado del operando. El operando debe ser de tipo aritmético o de puntero (o una expresión que se evalúe como un tipo aritmético o de puntero). El operando se convierte implícitamente al tipo `bool`. El resultado es **true** si el operando convertido es **false**; el resultado es **false** si el operando convertido es **true**. El resultado es de tipo `bool`.  
  
 Para una expresión *e*, la expresión unaria **!** *e* es equivalente a la expresión **(***e* `==` 0), excepto donde intervienen operadores sobrecargados.  
  
## <a name="operator-keyword-for-"></a>Palabra clave del operador para !  
 El **no** operador es el equivalente de texto de **!**. Hay dos maneras de obtener acceso a la **no** operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).  
  
## <a name="example"></a>Ejemplo  
  
```  
// expre_Logical_NOT_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 0;  
   if (!i)  
      cout << "i is zero" << endl;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Los operadores integrados de C++, prioridad y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores aritméticos unarios](../c-language/unary-arithmetic-operators.md)
