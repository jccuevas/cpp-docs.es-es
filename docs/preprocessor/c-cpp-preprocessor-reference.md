---
title: Referencia del preprocesador de C/C++
ms.date: 10/31/2019
helpviewer_keywords:
- preprocessor
- preprocessor, reference overview
ms.assetid: e4a52843-7016-4f6d-8b40-cb1ace18f805
ms.openlocfilehash: ef93f2cb98a033eed539ffc25559937b274d8a21
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754088"
---
# <a name="cc-preprocessor-reference"></a>Referencia del preprocesador de C/C++

La *referencia deC++ c/preprocesador* explica el preprocesador tal como se implementa en Microsoft C/.C++ El preprocesador realiza operaciones preliminares en archivos de C y C++ antes de pasarlos al compilador. Puede usar el preprocesador para realizar las siguientes acciones de manera condicional: compilar código, insertar archivos, especificar mensajes de error en tiempo de compilación y aplicar reglas específicas del equipo a secciones del código.

En Visual Studio 2019, la opción del compilador [/experimental: preprocesador](../build/reference/experimental-preprocessor.md) habilita una nueva implementación del preprocesador. La nueva implementación todavía está en curso y, por tanto, se considera experimental. Está previsto que finalmente sea compatible con C99, C11 y C++ 20. Para obtener más información, vea [información general del preprocesador experimental de MSVC](preprocessor-experimental-overview.md).

## <a name="in-this-section"></a>En esta sección

\ del [preprocesador](preprocessor.md)
Proporciona información general de los preprocesadores experimentales tradicionales y nuevos.

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)\
Describe las directivas, utilizadas normalmente para que los programas de origen sean fáciles de modificar y de compilar en diferentes entornos de ejecución.

[Operadores de preprocesador](../preprocessor/preprocessor-operators.md)\
Describe los cuatro operadores específicos del preprocesador usados en el contexto de la directiva `#define`.

[Macros predefinidas](../preprocessor/predefined-macros.md)\
Describe las macros tal como especifican ANSI y Microsoft C++.

[Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
Describe las directivas pragma, que proporcionan un método para que cada compilador ofrezca características específicas del equipo o del sistema operativo a la vez que conserva la compatibilidad total con los lenguajes C y C++.

## <a name="related-sections"></a>Secciones relacionadas

Referencia del lenguaje\ [ C++ ](../cpp/cpp-language-reference.md)
Proporciona material de referencia para la implementación de Microsoft del lenguaje C++.

[Referencia del lenguaje C](../c-language/c-language-reference.md)\
Proporciona material de referencia para la implementación de Microsoft del lenguaje C.

\ de [referencia de C/C++ Build](../build/reference/c-cpp-building-reference.md)
Proporciona vínculos a temas que describen las opciones del compilador y el vinculador.

[Proyectos de Visual Studio C++ :](../build/creating-and-managing-visual-cpp-projects.md)\
Describe la interfaz de usuario de Visual Studio que permite especificar los directorios en los que el sistema de proyectos buscará los archivos para el proyecto de C++.
