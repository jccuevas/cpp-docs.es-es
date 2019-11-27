---
title: Restricciones en los controladores de excepciones
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 030d444443b3a6e3e2e0ac0e015619046a76d562
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245157"
---
# <a name="restrictions-on-exception-handlers"></a>Restricciones en los controladores de excepciones

La limitación principal al uso de controladores de excepciones en el código es que no se puede usar una instrucción **goto** para saltar a un bloque de instrucciones **__try** . En su lugar, se debe especificar el bloque de instrucciones a través del flujo de control normal. Puede saltar fuera de un bloque de instrucciones de **__try** y anidar los controladores de excepciones que elija.

## <a name="see-also"></a>Vea también

[Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)