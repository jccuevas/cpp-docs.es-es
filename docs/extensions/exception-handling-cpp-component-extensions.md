---
title: Control de excepciones (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- structured exception handling [C++], managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
ms.openlocfilehash: b477f7355ee1f4f70a0ad3df8b85c4276c07d397
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516580"
---
# <a name="exception-handling--ccli-and-ccx"></a>Control de excepciones (C++/CLI y C++/CX)

Las aplicaciones compiladas con las opciones del compilador `/ZW` o `/clr` usan *excepciones* para controlar errores inesperados durante la ejecución de programas. En los siguientes temas se explica el control de excepciones en las aplicaciones de C++/CX o C++/CLI.

## <a name="in-this-section"></a>En esta sección

[Conceptos básicos del uso de excepciones administradas](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
Describe la producción de excepciones y el uso de bloques **try**/**catch**.

[Diferencias en el comportamiento del control de excepciones en /CLR](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
Explica las diferencias respecto al comportamiento estándar del control de excepciones de C++.

[finally](../dotnet/finally.md)<br/>
Explica cómo usar la palabra clave finally.

[Cómo: Definir e instalar un controlador de excepciones global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Muestra cómo se pueden capturar las excepciones no controladas.

[Cómo: Detectar excepciones en código nativo iniciadas desde MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
Explica cómo detectar excepciones CLR y C++ en código nativo.

[Cómo: Definir e instalar un controlador de excepciones global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Muestra cómo detectar todas las excepciones no controladas.

## <a name="related-sections"></a>Secciones relacionadas

[Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)<br/>
Describe el control de excepciones en C++ estándar.

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)