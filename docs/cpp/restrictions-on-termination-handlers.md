---
title: Restricciones de los controladores de finalización
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: 6c39407270037756c55dc42aed80e1d04616c9ee
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246380"
---
# <a name="restrictions-on-termination-handlers"></a>Restricciones de los controladores de finalización

You cannot use a **goto** statement to jump into a **__try** statement block or a **__finally** statement block. En su lugar, se debe especificar el bloque de instrucciones a través del flujo de control normal. (You can, however, jump out of a **__try** statement block.) Also, you cannot nest an exception handler or termination handler inside a **__finally** block.

Además, algunos tipos de código permitidos en un controlador de finalización generan resultados cuestionables, por lo que deben utilizarse con precaución, si se utilizan. One is a **goto** statement that jumps out of a **__finally** statement block. Si el bloque se ejecuta como parte de una finalización normal, no sucede nada inusual. Pero si el sistema está desenredando la pila, el desenredado se detiene y la función actual obtiene el control como si no hubiera una finalización anómala.

A **return** statement inside a **__finally** statement block presents roughly the same situation. El control se devuelve al llamador inmediato de la función que contiene el controlador de finalización. Si el sistema estaba desenredando la pila, este proceso se detiene y el programa continúa como si no se hubiera producido una excepción.

## <a name="see-also"></a>Vea también

[Writing a termination handler](../cpp/writing-a-termination-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)