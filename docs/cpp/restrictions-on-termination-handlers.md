---
title: Restricciones de los controladores de finalización
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: befe181a41ed418a4a824b131e741a9f02f90e38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179073"
---
# <a name="restrictions-on-termination-handlers"></a>Restricciones de los controladores de finalización

No se puede usar una instrucción **goto** para saltar a un bloque de instrucciones **__try** o un bloque de instrucciones **__finally** . En su lugar, se debe especificar el bloque de instrucciones a través del flujo de control normal. (Sin embargo, puede saltar fuera de un bloque de instrucciones **__try** ). Además, no puede anidar un controlador de excepciones ni un controlador de finalización dentro de un bloque **__finally** .

Además, algunos tipos de código permitidos en un controlador de finalización generan resultados cuestionables, por lo que deben utilizarse con precaución, si se utilizan. Una es una instrucción **goto** que salta de un bloque de instrucciones **__finally** . Si el bloque se ejecuta como parte de una finalización normal, no sucede nada inusual. Pero si el sistema está desenredando la pila, el desenredado se detiene y la función actual obtiene el control como si no hubiera una finalización anómala.

Una instrucción **Return** dentro de un bloque de instrucciones de **__finally** presenta aproximadamente la misma situación. El control se devuelve al llamador inmediato de la función que contiene el controlador de finalización. Si el sistema estaba desenredando la pila, este proceso se detiene y el programa continúa como si no se hubiera producido una excepción.

## <a name="see-also"></a>Consulte también

[Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
