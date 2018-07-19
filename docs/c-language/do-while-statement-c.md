---
title: do-while (Instrucción) (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- do
- while
dev_langs:
- C++
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0638e10d87ed52de49b027aea1e06bee838867d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385437"
---
# <a name="do-while-statement-c"></a>do-while (Instrucción) (C)
La instrucción `do-while` permite repetir una instrucción o una instrucción compuesta hasta que una expresión especificada sea false.  
  
## <a name="syntax"></a>Sintaxis  
 *iteration-statement*:  
 **do**  *statement*  **while (**  *expression*  **) ;**  
  
 El elemento *expression* en una instrucción `do-while` se evalúa después de que se ejecute el cuerpo del bucle. Por consiguiente, el cuerpo del bucle se ejecuta siempre al menos una vez.  
  
 *expression* debe tener un tipo aritmético o de puntero. La ejecución continúa de la siguiente manera:  
  
1.  Se ejecuta el cuerpo de instrucción.  
  
2.  A continuación, se evalúa *expression*. Si *expression* es false, la instrucción `do-while` finaliza y el control pasa a la siguiente instrucción del programa. Si *expression* es true (distinta de cero), el proceso se repite a partir del paso 1.  
  
 La instrucción `do-while` también puede finalizar cuando se ejecuta una instrucción **break**, `goto` o `return` dentro del cuerpo de la instrucción.  
  
 Este es un ejemplo de la instrucción `do-while`:  
  
```  
do   
{  
    y = f( x );  
    x--;  
} while ( x > 0 );  
```  
  
 En esta instrucción `do-while`, se ejecutan las dos instrucciones `y = f( x );` y `x--;`, independientemente del valor inicial de `x`. A continuación `x > 0` se evalúa. Si `x` es mayor que 0, el cuerpo de instrucción se ejecuta de nuevo y `x > 0` se evalúa de nuevo. El cuerpo de instrucción se ejecuta repetidamente mientras `x` siga siendo mayor que 0. La ejecución de la instrucción `do-while` finaliza cuando `x` se convierte en 0 o negativo. El cuerpo del bucle se ejecuta al menos una vez.  
  
## <a name="see-also"></a>Vea también  
 [do-while (Instrucción) (C++)](../cpp/do-while-statement-cpp.md)