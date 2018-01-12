---
title: "Uso de nombre de función sin () No genera código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c03706be0b9853cbbdebe79b58e410f7237692ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-function-name-without--produces-no-code"></a>La utilización de un nombre de función sin () no genera código
Cuando se utiliza el nombre de una función declarado en el programa sin paréntesis, el compilador no genera código. Esto ocurre independientemente de si la función toma parámetros porque el compilador calcula la dirección de la función; Sin embargo, dado que el operador de llamada de función "()" no está presente, se realiza ninguna llamada. El resultado es similar al siguiente:  
  
```  
// compile with /Wall to generate a warning  
int a;  
a;      // no code generated here either  
```  
  
 En Visual C++, incluso con el nivel de advertencia 4, genera ninguna salida de diagnóstico. Se genera ninguna advertencia; no se genera ningún código.  
  
 El código de ejemplo siguiente se compila (con una advertencia) y vincula correctamente sin errores, pero no produce código en referencia a `funcn( )`. Para que funcione correctamente, agregue el operador de llamada de función "()".  
  
```  
#include <stdio.h>  
void funcn();  
  
int main() {  
   funcn;      /* missing function call operator;   
                  call will fail.  Use funcn() */  
   }  
  
void funcn() {  
   printf("\nHello World\n");  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Optimizar el código](../../build/reference/optimizing-your-code.md)