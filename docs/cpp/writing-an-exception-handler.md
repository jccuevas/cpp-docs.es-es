---
title: Escribir un controlador de excepciones
ms.date: 11/04/2016
helpviewer_keywords:
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
ms.openlocfilehash: 201dcaa6a90584d1f9535df11d5722a37bdceb89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187289"
---
# <a name="writing-an-exception-handler"></a>Escribir un controlador de excepciones

Los controladores de excepciones se utilizan normalmente para responder a errores específicos. Puede utilizar la sintaxis del control de excepciones para filtrar todas las excepciones distintas de las que sabe cómo administrar. Las demás excepciones se deben pasar a otros controladores (posiblemente en la biblioteca en tiempo de ejecución o el sistema operativo) creados para buscar esas excepciones concretas.

Los controladores de excepciones utilizan la instrucción try-except.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [La instrucción try-except](../cpp/try-except-statement.md)

- [Escribir un filtro de excepciones](../cpp/writing-an-exception-filter.md)

- [Generar excepciones de software](../cpp/raising-software-exceptions.md)

- [Excepciones de hardware](../cpp/hardware-exceptions.md)

- [Restricciones en los controladores de excepciones](../cpp/restrictions-on-exception-handlers.md)

## <a name="see-also"></a>Consulte también

[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
