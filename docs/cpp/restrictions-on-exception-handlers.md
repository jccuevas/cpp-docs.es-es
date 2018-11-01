---
title: Restricciones de los controladores de excepciones
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 7d5bf20da61f4b9f5012b7f2aab932dfc904c302
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573997"
---
# <a name="restrictions-on-exception-handlers"></a>Restricciones de los controladores de excepciones

La limitación principal de utilizar controladores de excepciones en código es que no se puede usar un **goto** instrucción para saltar en un **__try** bloque de instrucciones. En su lugar, se debe especificar el bloque de instrucciones a través del flujo de control normal. Puede saltar fuera de un **__try** instrucción en bloques y anidar los controladores de excepciones como desee.

## <a name="see-also"></a>Vea también

[Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)