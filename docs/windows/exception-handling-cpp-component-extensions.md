---
title: Control de excepciones (extensiones de componente de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling, managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- managed exceptions
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 566ed55df84accef0c3e5308e750a2684c36b91c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606799"
---
# <a name="exception-handling--c-component-extensions"></a>Control de excepciones (Extensiones de componentes de C++)

Las aplicaciones compiladas con la `/ZW` opción del compilador o `/clr` opción del compilador ambos usan *excepciones* para controlar los errores inesperados durante la ejecución del programa. Los temas siguientes tratan el control de excepciones en cualquier C++ / c++ / CX o c++ / aplicaciones de la CLI.

## <a name="in-this-section"></a>En esta sección

[Conceptos básicos del uso de excepciones administradas](../dotnet/basic-concepts-in-using-managed-exceptions.md)  
Describe excepciones y el uso **intente**/**catch** bloques.

[Diferencias de comportamiento en/CLR de control de excepciones](../dotnet/differences-in-exception-handling-behavior-under-clr.md)  
Describe las diferencias en el comportamiento estándar de control de excepciones de C++.

[finally](../dotnet/finally.md)  
Describe cómo utilizar la palabra clave finally.

[Cómo: Definir e instalar un controlador de excepciones global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
Muestra las excepciones no controladas de cómo se pueden capturar.

[Cómo: Detectar excepciones en código nativo iniciadas desde MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)  
Describe cómo detectar las excepciones de CLR y C++ en código nativo.

[Cómo: Definir e instalar un controlador de excepciones global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
Muestra cómo detectar las excepciones no controladas de todo.

## <a name="related-sections"></a>Secciones relacionadas

[Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)  
Describe el control de excepciones en C++.

## <a name="see-also"></a>Vea también

[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)