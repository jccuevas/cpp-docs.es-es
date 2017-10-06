---
title: "Restricciones en los controladores de terminación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
ms.openlocfilehash: 0c7be69cf8371b354f13863177d48cbb00f647b0
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="restrictions-on-termination-handlers"></a>Restricciones de los controladores de finalización
No puede utilizar una instrucción `goto` para saltar dentro de un bloque de instrucciones `__try` o un bloque de instrucciones `__finally`. En su lugar, se debe especificar el bloque de instrucciones a través del flujo de control normal. (Sin embargo, puede saltar fuera de un bloque de instrucciones `__try`). Además, no puede anidar un controlador de excepciones ni un controlador de finalización dentro de un bloque de instrucciones `__finally`.  
  
 Además, algunos tipos de código permitidos en un controlador de finalización generan resultados cuestionables, por lo que deben utilizarse con precaución, si se utilizan. Uno de ellos es una instrucción `goto` que salta fuera de un bloque de instrucciones `__finally`. Si el bloque se ejecuta como parte de una finalización normal, no sucede nada inusual. Pero si el sistema está desenredando la pila, el desenredado se detiene y la función actual obtiene el control como si no hubiera una finalización anómala.  
  
 Una instrucción `return` dentro de un bloque de instrucciones `__finally` presenta casi la misma situación. El control se devuelve al llamador inmediato de la función que contiene el controlador de finalización. Si el sistema estaba desenredando la pila, este proceso se detiene y el programa continúa como si no se hubiera producido una excepción.  
  
## <a name="see-also"></a>Vea también  
 [Escribir un controlador de terminación](../cpp/writing-a-termination-handler.md)   
 [Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
