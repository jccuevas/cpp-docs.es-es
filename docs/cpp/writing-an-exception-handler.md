---
title: Escribir un controlador de excepciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8956bb673c756224a886dede90cf23d84c3f20c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050975"
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