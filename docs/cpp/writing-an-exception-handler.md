---
title: Escribir un controlador de excepciones
ms.date: 11/04/2016
helpviewer_keywords:
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
ms.openlocfilehash: 6f1bcecf3aaed2bf2b7ebbe511f11cdb5ec1ca5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644787"
---
# <a name="writing-an-exception-handler"></a>Escribir un controlador de excepciones

Los controladores de excepciones se utilizan normalmente para responder a errores específicos. Puede utilizar la sintaxis del control de excepciones para filtrar todas las excepciones distintas de las que sabe cómo administrar. Las demás excepciones se deben pasar a otros controladores (posiblemente en la biblioteca en tiempo de ejecución o el sistema operativo) creados para buscar esas excepciones concretas.

Los controladores de excepciones utilizan la instrucción try-except.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Try-except instrucción](../cpp/try-except-statement.md)

- [Escribir un filtro de excepción](../cpp/writing-an-exception-filter.md)

- [Generar excepciones de software](../cpp/raising-software-exceptions.md)

- [Excepciones de hardware](../cpp/hardware-exceptions.md)

- [Restricciones en los controladores de excepción](../cpp/restrictions-on-exception-handlers.md)

## <a name="see-also"></a>Vea también

[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)