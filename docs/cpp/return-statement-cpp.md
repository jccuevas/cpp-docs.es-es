---
title: "devolver la instrucción) (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- return_cpp
dev_langs:
- C++
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d6857983412b2037b8958c2b1a0bee9d9dda053
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="return-statement-c"></a>return (Instrucción) (C++)
Finaliza la ejecución de una función y devuelve el control a la función de llamada (o al sistema operativo si se transfiere el control de la función `main`). La ejecución se reanuda en la función de llamada, en el punto que sigue inmediatamente a la llamada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
return [expression];  
```  
  
## <a name="remarks"></a>Comentarios  
 La cláusula `expression`, si está presente, se convierte al tipo especificado en la declaración de función, como si se realizara una inicialización. La conversión del tipo de la expresión al tipo `return` de la función puede crear objetos temporales. Para obtener más información acerca de cómo y cuándo se crean objetos temporales, consulte [objetos temporales](../cpp/temporary-objects.md).  
  
 El valor de la cláusula `expression` se devuelve a la función de llamada. Si se omite la expresión, el valor devuelto de la función es indefinido. Constructores y destructores y funciones de tipo `void`, no se puede especificar una expresión en el `return` instrucción. Las funciones de todos los demás tipos deben especificar una expresión en la instrucción `return`.  
  
 Cuando el flujo de control sale del bloque que incluye la definición de función, el resultado es el mismo que si se hubiera ejecutado una instrucción `return` sin una expresión. Esto no es válido para las funciones que se declaran como si devolvieran un valor.  
  
 Una función puede tener cualquier número de instrucciones `return`.  
  
 En el ejemplo siguiente se utiliza una expresión con una instrucción `return` para obtener el mayor de dos enteros.  
  
## <a name="example"></a>Ejemplo  
  
```  
// return_statement2.cpp  
#include <stdio.h>  
  
int max ( int a, int b )  
{  
   return ( a > b ? a : b );  
}  
  
int main()  
{  
    int nOne = 5;  
    int nTwo = 7;  
  
    printf_s("\n%d is bigger\n", max( nOne, nTwo ));  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Jump Statements](../cpp/jump-statements-cpp.md)  (Instrucciones de salto)  
 [Palabras clave](../cpp/keywords-cpp.md)