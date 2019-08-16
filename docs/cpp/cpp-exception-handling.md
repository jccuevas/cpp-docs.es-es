---
title: Control de excepciones de C++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
ms.openlocfilehash: bbdec38bf722ebb1e188af408bf3a413f6d6b8b7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222157"
---
# <a name="c-exception-handling"></a>Control de excepciones de C++

El lenguaje C++ proporciona compatibilidad integrada para producir y detectar excepciones. Al programar en C++, casi siempre se debe utilizar la compatibilidad con excepciones de C++ integrada como se describe en esta sección.

Para habilitar en el código de control de excepciones de C++, use [/EHsc](../build/reference/eh-exception-handling-model.md).

## <a name="in-this-section"></a>En esta sección

Esta descripción del control de excepciones de C++ incluye lo siguiente:

- [Try, catch y throw (instrucciones)](../cpp/try-throw-and-catch-statements-cpp.md)

- [Cómo se evalúan los bloques Catch](../cpp/how-catch-blocks-are-evaluated-cpp.md)

- [Excepciones y desenredo de pila](../cpp/exceptions-and-stack-unwinding-in-cpp.md)

- [Especificaciones de excepción](../cpp/exception-specifications-throw-cpp.md)

- [noexcept](../cpp/noexcept-cpp.md)

- [Excepciones de C++ no controladas](../cpp/unhandled-cpp-exceptions.md)

- [Mezclar excepciones de C (estructuradas) y de C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)

## <a name="support-for-earlier-mfc-exceptions"></a>Compatibilidad con excepciones MFC anteriores

A partir de la versión 4.0, MFC empezó a usar el mecanismo de control de excepciones de C++. Aunque se recomienda utilizar el control de excepciones de C++ en el código nuevo, la versión 4.0 de MFC y las versiones posteriores conservan las macros de versiones anteriores de MFC, por lo que el código anterior no resultará dañado. También se pueden combinar las macros y el nuevo mecanismo. Para obtener información sobre cómo mezclar macros y C++ excepción tratamiento y cómo convertir antiguo código para usar el nuevo mecanismo, consulte los artículos [excepciones: Uso de Macros MFC y C++ excepciones](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) y [excepciones: Convertir desde Macros de excepción de MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md). Las macros de excepciones de MFC anteriores, si todavía las utiliza, se evalúan como palabras clave de excepciones de C++. Consulte [excepciones: Cambios en las Macros de excepción en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

## <a name="see-also"></a>Vea también

[Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)