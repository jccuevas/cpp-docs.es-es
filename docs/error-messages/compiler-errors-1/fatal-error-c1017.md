---
title: Error irrecuperable C1017 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1017
dev_langs:
- C++
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08433109a959b324621e9c837e67cf529d9f6fdb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199724"
---
# <a name="fatal-error-c1017"></a>Error irrecuperable C1017
expresión constante de tipo entero no válida  
  
 La expresión en una `#if` directiva no existe o no se evaluaran como una constante.  
  
 Constantes que se definen mediante `#define` deben tener valores que se evalúan como una constante entera si se utilizan en una `#if`, `#elif`, o `#else` directiva.  
  
 El ejemplo siguiente genera C1017:  
  
```  
// C1017.cpp  
#define CONSTANT_NAME "YES"  
#if CONSTANT_NAME   // C1017  
#endif  
```  
  
 Posible resolución:  
  
```  
// C1017b.cpp  
// compile with: /c  
#define CONSTANT_NAME 1  
#if CONSTANT_NAME  
#endif  
```  
  
 Dado que `CONSTANT_NAME` se evalúa como una cadena y no es un entero, el `#if` directiva generará el error irrecuperable C1017.  
  
 En otros casos, el preprocesador se evalúa como una constante definida como cero. Esto puede provocar resultados no deseados, tal como se muestra en el ejemplo siguiente. `YES` no está definido, por lo que se evalúa como cero. La expresión `#if` `CONSTANT_NAME` se evalúa como false y el código que se utilizará en `YES` sea quitado por el preprocesador. `NO` También está definido (cero), de modo que `#elif` `CONSTANT_NAME==NO` se evalúa como true (`0 == 0`), lo que el preprocesador dejará el código en el `#elif` parte de la instrucción, justo lo contrario de lo esperado.  
  
```  
// C1017c.cpp  
// compile with: /c  
#define CONSTANT_NAME YES  
#if CONSTANT_NAME  
   // Code to use on YES...  
#elif CONSTANT_NAME==NO  
   // Code to use on NO...  
#endif  
```  
  
 Para ver exactamente cómo controla el compilador las directivas de preprocesador, utilice [/P](../../build/reference/p-preprocess-to-a-file.md), [/E](../../build/reference/e-preprocess-to-stdout.md), o [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).