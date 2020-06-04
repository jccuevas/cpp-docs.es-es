---
title: /Zc:__cplusplus (Habilitar macro __cplusplus actualizada)
ms.date: 05/16/2019
f1_keywords:
- /Zc:__cplusplus
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
ms.openlocfilehash: 43392438eabc7cc7f6decb1349d112a0ce5bd0f5
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837552"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc:__cplusplus (Habilitar macro __cplusplus actualizada)

La opción del compilador **/Zc:__cplusplus** habilita la macro de preprocesador **\_\_cplusplus** para notificar un valor actualizado para la compatibilidad con estándares recientes del lenguaje C++. De forma predeterminada, Visual Studio siempre devuelve el valor "199711L" para la macro de preprocesador **\_\_cplusplus**.

## <a name="syntax"></a>Sintaxis

> **/Zc:__cplusplus**[ **-** ]

## <a name="remarks"></a>Comentarios

La macro de preprocesador **\_\_cplusplus** se usa habitualmente para notificar la compatibilidad con una versión concreta del estándar C++. Como parece que una gran cantidad de código existente depende de que el valor de esta macro coincida con "199711L", el compilador no cambia el valor de la macro a menos que lo haga de forma explícita mediante la opción del compilador **/Zc:__cplusplus**. La opción **/Zc:__cplusplus** está disponible a partir de Visual Studio 2017 versión 15.7 y está desactivada de forma predeterminada. En versiones anteriores de Visual Studio, y de forma predeterminada, o bien si se especifica **/Zc:__cplusplus-** , Visual Studio devuelve el valor "199711L" para la macro de preprocesador **\_\_cplusplus**. La opción [/permissive-](permissive-standards-conformance.md) no habilita **/Zc:__cplusplus**.

Cuando se habilita la opción **/Zc:__cplusplus**, el valor notificado por la macro **\_\_cplusplus** depende del valor del modificador de versión [/std](std-specify-language-standard-version.md). En esta tabla se muestran los posibles valores para la macro:

|Modificador /Zc:__cplusplus|Modificador /std:c++|Valor __cplusplus|
|-|-|-|
Zc:__cplusplus|/std:c++14 (valor predeterminado)|201402L
Zc:__cplusplus|/std:c++17|201703L
Zc:__cplusplus|/std:c++latest|201704L
Zc:__cplusplus- (deshabilitado)|Cualquier valor|199711L
No especificado|Cualquier valor|199711L

El compilador no admite modificadores de estándares para C++98, C++03 ni C++11.

Para obtener una detección más precisa de los cambios realizados en el conjunto de herramientas del compilador, use la macro predefinida [_MSC_VER](../../preprocessor/predefined-macros.md). El valor de esta macro integrada se incrementa para cada actualización del conjunto de herramientas en Visual Studio 2017 y versiones posteriores. La macro predefinida [_MSVC_LANG](../../preprocessor/predefined-macros.md) notifica a la versión del estándar si la opción **/Zc:__cplusplus** está habilitada o deshabilitada. Cuando **/Zc:__cplusplus** está habilitada, `__cplusplus == _MSVC_LANG`.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para establecer esta opción del compilador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **C /C++** > **Línea de comandos**.

1. Agregue **/Zc:__cplusplus** o **/Zc:__cplusplus-** al panel **Opciones adicionales:** .

## <a name="see-also"></a>Vea también

- [/Zc (Ajuste)](zc-conformance.md)
- [/std (Especificar la versión estándar del lenguaje)](std-specify-language-standard-version.md)
- [Macros predefinidas](../../preprocessor/predefined-macros.md)
