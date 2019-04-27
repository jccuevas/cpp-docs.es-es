---
title: Escribir un controlador de finalización
ms.date: 11/04/2016
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
ms.openlocfilehash: f0b994075a8d59ce5d0955f10bf8c61d357d2db9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209473"
---
# <a name="writing-a-termination-handler"></a>Escribir un controlador de finalización

A diferencia de los controladores de excepciones, los controladores de terminación se ejecutan siempre, independientemente de si el bloque de código protegido ha finalizado normalmente. El único propósito del controlador de terminación debe ser garantizar que los recursos, como la memoria, los identificadores y los archivos, se cierran correctamente independientemente de cómo termine de ejecutarse una sección de código.

Los controladores de terminación utilizan la instrucción try-finally.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [La instrucción try-finally](../cpp/try-finally-statement.md)

- [Limpiar recursos](../cpp/cleaning-up-resources.md)

- [Cronología de las acciones de control de excepciones](../cpp/timing-of-exception-handling-a-summary.md)

- [Restricciones en los controladores de terminación](../cpp/restrictions-on-termination-handlers.md)

## <a name="see-also"></a>Vea también

[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)