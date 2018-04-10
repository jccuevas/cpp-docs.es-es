---
title: Restricciones en los controladores de terminación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71486b167f4e9939d4913b3660ed3513dc02b8f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="restrictions-on-termination-handlers"></a>Restricciones de los controladores de finalización
No puede utilizar una instrucción `goto` para saltar dentro de un bloque de instrucciones `__try` o un bloque de instrucciones `__finally`. En su lugar, se debe especificar el bloque de instrucciones a través del flujo de control normal. (Sin embargo, puede saltar fuera de un bloque de instrucciones `__try`). Además, no puede anidar un controlador de excepciones ni un controlador de finalización dentro de un bloque de instrucciones `__finally`.  
  
 Además, algunos tipos de código permitidos en un controlador de finalización generan resultados cuestionables, por lo que deben utilizarse con precaución, si se utilizan. Uno de ellos es una instrucción `goto` que salta fuera de un bloque de instrucciones `__finally`. Si el bloque se ejecuta como parte de una finalización normal, no sucede nada inusual. Pero si el sistema está desenredando la pila, el desenredado se detiene y la función actual obtiene el control como si no hubiera una finalización anómala.  
  
 Una instrucción `return` dentro de un bloque de instrucciones `__finally` presenta casi la misma situación. El control se devuelve al llamador inmediato de la función que contiene el controlador de finalización. Si el sistema estaba desenredando la pila, este proceso se detiene y el programa continúa como si no se hubiera producido una excepción.  
  
## <a name="see-also"></a>Vea también  
 [Escribir un controlador de terminación](../cpp/writing-a-termination-handler.md)   
 [Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)