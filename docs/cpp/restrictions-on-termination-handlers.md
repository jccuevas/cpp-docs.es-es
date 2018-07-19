---
title: Restricciones en los controladores de terminación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 969930c3918cdc0d2e38747796279c7135aba5a7
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941345"
---
# <a name="restrictions-on-termination-handlers"></a>Restricciones de los controladores de finalización
No puede usar un **goto** instrucción para saltar en un **__try** bloque de instrucciones o un **__finally** bloque de instrucciones. En su lugar, se debe especificar el bloque de instrucciones a través del flujo de control normal. (Sin embargo, puede saltar fuera de un **__try** bloque de instrucciones.) Además, no se pueden anidar un controlador de excepciones o el controlador de finalización dentro un **__finally** bloque.  
  
 Además, algunos tipos de código permitidos en un controlador de finalización generan resultados cuestionables, por lo que deben utilizarse con precaución, si se utilizan. Uno es un **goto** instrucción que salta fuera de un **__finally** bloque de instrucciones. Si el bloque se ejecuta como parte de una finalización normal, no sucede nada inusual. Pero si el sistema está desenredando la pila, el desenredado se detiene y la función actual obtiene el control como si no hubiera una finalización anómala.  
  
 Un **devolver** instrucción dentro de un **__finally** bloque de instrucciones presenta casi la misma situación. El control se devuelve al llamador inmediato de la función que contiene el controlador de finalización. Si el sistema estaba desenredando la pila, este proceso se detiene y el programa continúa como si no se hubiera producido una excepción.  
  
## <a name="see-also"></a>Vea también  
 [Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)   
 [Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)