---
title: 'Operador lógico de negación: ! | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f911c6f01dfc188c26355a3749d8a130f0d6951
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403594"
---
# <a name="logical-negation-operator-"></a>Operador lógico de negación: !
## <a name="syntax"></a>Sintaxis  
  
```  
! cast-expression  
```  
  
## <a name="remarks"></a>Comentarios  
 El operador lógico de negación (**!**) invierte el significado del operando. El operando debe ser de tipo aritmético o de puntero (o una expresión que se evalúe como un tipo aritmético o de puntero). El operando se convierte implícitamente al tipo **bool**. El resultado es TRUE si el operando convertido es FALSE. el resultado es FALSE si el operando convertido es TRUE. El resultado es de tipo **bool**.  
  
 Para una expresión *e*, la expresión unaria **! *** e* es equivalente a la expresión **(*** e* `==` 0), excepto donde intervienen operadores sobrecargados.  
  
## <a name="operator-keyword-for-"></a>Palabra clave del operador para !  
 El **no** operador es el equivalente textual de **!**. Hay dos maneras de acceder a la **no** operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
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
 [Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores aritméticos unarios](../c-language/unary-arithmetic-operators.md)