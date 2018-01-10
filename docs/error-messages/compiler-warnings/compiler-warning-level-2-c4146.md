---
title: Advertencia de compilador (nivel 2) de la advertencia C4146 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4146
dev_langs: C++
helpviewer_keywords: C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d7a9a67beb4dc122c25318c1796e22a4c35dbe38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4146"></a>Advertencia de compilador (nivel 2) de la advertencia C4146
operador unario menos aplicado a un tipo sin signo, resultado sigue sin firmar  
  
 Tipos sin signo pueden contener valores de solo positivo, por lo que el operador unario menos (negación) no suele tener sentido cuando se aplica a un tipo sin signo. El operando y lo resultados no son negativos.  
  
 En la práctica, esto se produce cuando el programador intenta expresar el valor de entero mínimo, que es -2147483648. Este valor no puede escribirse como -2147483648 porque la expresión se procesa en dos fases:  
  
1.  Se evalúa el número 2147483648. Dado que es mayor que el valor de entero máximo de 2147483647, el tipo de 2147483648 no es [int](../../c-language/integer-types.md), pero `unsigned int`.  
  
2.  Unaria se aplica al valor, con un resultado sin signo, que también resulta ser 2147483648.  
  
 El tipo sin signo del resultado puede provocar un comportamiento inesperado. Si se utiliza el resultado en una comparación, una comparación unsigned podría utilizarse, por ejemplo, cuando el otro operando es un `int`. Esto explica por qué el programa de ejemplo siguiente imprime sólo una línea.  
  
 La segunda línea esperada, `1 is greater than the most negative int`, no se imprime porque `((unsigned int)1) > 2147483648` es false.  
  
 Puede evitar la advertencia C4146 usando INT_MIN de limits.h, que tiene el tipo **firmado int**.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4146:  
  
```  
// C4146.cpp  
// compile with: /W2  
#include <stdio.h>  
  
void check(int i)   
{  
    if (i > -2147483648)   // C4146  
        printf_s("%d is greater than the most negative int\n", i);  
}  
  
int main()   
{  
    check(-100);  
    check(1);  
}  
```